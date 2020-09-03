---
title: 'Cómo: diagnosticar el rendimiento de una extensión | Microsoft Docs'
ms.date: 11/08/2016
ms.topic: how-to
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
author: BertanAygun
ms.author: bertaygu
manager: jillfra
ms.workload:
- bertaygu
ms.openlocfilehash: 542d8a6d6d90091aa7a800ef18f847fea6b1a81c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905904"
---
# <a name="measuring-extension-impact-in-startup"></a>Medir el impacto de la extensión en el inicio

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>Céntrese en el rendimiento de las extensiones en Visual Studio 2017

En función de los comentarios de los clientes, una de las áreas de enfoque para la versión 2017 de Visual Studio ha sido el rendimiento de inicio y carga de soluciones. Como el equipo de la plataforma de Visual Studio, hemos estado trabajando para mejorar el rendimiento de la carga de inicio y de la solución. En general, nuestras medidas sugieren que las extensiones instaladas también pueden tener un impacto considerable en esos escenarios.

Para ayudar a los usuarios a comprender este impacto, hemos agregado una nueva característica en Visual Studio para notificar a los usuarios de extensiones lentas. En ocasiones, Visual Studio detecta una nueva extensión que ralentiza la carga o el inicio de la solución. Cuando se detecta una ralentización, los usuarios verán una notificación en el IDE que les apunta al nuevo cuadro de diálogo "administrar el rendimiento de Visual Studio". También se puede tener acceso a este cuadro de diálogo en el menú Ayuda para examinar las extensiones detectadas previamente.

![administrar el rendimiento de Visual Studio](media/manage-performance.png)

Este documento pretende ayudar a los desarrolladores de extensiones a describir cómo se calcula el impacto de la extensión. Este documento también describe cómo se puede analizar el impacto de la extensión localmente. El análisis local del impacto de la extensión determinará si se puede mostrar una extensión como una extensión que afecte al rendimiento.

> [!NOTE]
> Este documento se centra en el impacto de las extensiones en el inicio y la carga de la solución. Las extensiones también afectan al rendimiento de Visual Studio cuando hacen que la interfaz de usuario deje de responder. Para obtener más información sobre este tema, consulte [Cómo: diagnosticar retrasos de la interfaz de usuario causados por extensiones](how-to-diagnose-ui-delays-caused-by-extensions.md).

## <a name="how-extensions-can-impact-startup"></a>Cómo pueden afectar las extensiones al inicio

Una de las formas más comunes de que las extensiones afecten al rendimiento de inicio consiste en elegir cargar automáticamente en uno de los contextos de la interfaz de usuario de inicio conocidos, como NoSolutionExists o ShellInitialized. Estos contextos de la interfaz de usuario se activan durante el inicio. Los paquetes que incluyan el `ProvideAutoLoad` atributo en su definición con esos contextos se cargarán e inicializarán en ese momento.

Cuando se mide el impacto de una extensión, nos centraremos principalmente en el tiempo invertido por las extensiones que optan por cargar automáticamente en los contextos anteriores. Los tiempos medidos se incluirán pero no se limitarán a:

* Carga de ensamblados de extensión para paquetes sincrónicos
* Tiempo empleado en el constructor de clase de paquete para paquetes sincrónicos
* Tiempo transcurrido en el método de inicialización de paquetes (o SetSite) para paquetes sincrónicos
* En el caso de los paquetes asincrónicos, las operaciones anteriores se ejecutan en el subproceso en segundo plano.  Como tal, las operaciones se excluyen de la supervisión.
* Tiempo empleado en cualquier trabajo asincrónico programado durante la inicialización del paquete para ejecutarse en el subproceso principal
* Tiempo empleado en los controladores de eventos, concretamente en el shell de activación de contexto inicializado o en el cambio de estado inerte del shell
* A partir de Visual Studio 2017 Update 3, también comenzaremos a supervisar el tiempo invertido en llamadas inactivas antes de que se inicialice el shell. Las operaciones largas en los controladores inactivos también causan un IDE que no responde y contribuyen al tiempo de inicio percibido por el usuario.

Hemos agregado muchas características a partir de Visual Studio 2015. Estas características ayudan a quitar la necesidad de cargar paquetes para cargarlos automáticamente. Las características también posponen la necesidad de que los paquetes se carguen en casos más específicos. Estos casos incluyen ejemplos en los que los usuarios serían más específicos para usar la extensión o reducir el impacto de la extensión cuando se cargan automáticamente.

Puede encontrar más detalles sobre estas características en los siguientes documentos:

[Contextos de la interfaz de usuario basada en reglas](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md): un motor basado en reglas más completo creado en torno a los contextos de la interfaz de usuario permite crear contextos personalizados basados en tipos de proyecto, sabores y atributos. Los contextos personalizados se pueden usar para cargar un paquete durante escenarios más específicos. Estos escenarios específicos incluyen la presencia de un proyecto con una capacidad específica en lugar de un inicio. Los contextos personalizados también permiten que [la visibilidad del comando esté ligada a un contexto personalizado](visibilityconstraints-element.md) basado en componentes del proyecto u otros términos disponibles. Esta característica elimina la necesidad de cargar un paquete para registrar un controlador de consulta de estado de comando.

[Compatibilidad con paquetes asincrónicos](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md): la nueva clase base AsyncPackage de visual Studio 2015 permite que los paquetes de Visual Studio se carguen en segundo plano de forma asincrónica si un atributo autoload o una consulta de servicio asincrónica solicitó la carga del paquete. Esta carga en segundo plano permite que el IDE siga respondiendo. El IDE responde incluso mientras la extensión se inicializa en segundo plano y los escenarios críticos, como el inicio y la carga de la solución, no se verán afectados.

[Servicios asincrónicos](how-to-provide-an-asynchronous-visual-studio-service.md): con compatibilidad con paquetes asincrónicos, también hemos agregado compatibilidad para consultar los servicios de forma asincrónica y poder registrar los servicios asincrónicos. Lo que es más importante, estamos trabajando en la conversión de los servicios principales de Visual Studio para admitir consultas asincrónicas, de modo que la mayoría del trabajo en una consulta asincrónica se produzca en subprocesos en segundo plano. SComponentModel (host de MEF de Visual Studio) es uno de los servicios principales que ahora admiten la consulta asincrónica para permitir que las extensiones admitan completamente la carga asincrónica.

## <a name="reducing-impact-of-auto-loaded-extensions"></a>Reducir el impacto de las extensiones cargadas automáticamente

Si un paquete todavía debe cargarse automáticamente en el inicio, es importante minimizar el trabajo realizado durante la inicialización del paquete. Minimizar el trabajo de inicialización del paquete reduce las posibilidades de que la extensión afecte al inicio.

Algunos ejemplos que podrían hacer que la inicialización del paquete sea caro:

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>Uso de la carga de paquetes sincrónicos en lugar de la carga de paquetes asincrónica

Dado que los paquetes sincrónicos se cargan en el subproceso principal de forma predeterminada, se recomienda que los propietarios de extensiones que tengan paquetes cargados automáticamente usen la clase base del paquete asincrónico, como se mencionó anteriormente. El cambio de un paquete cargado automáticamente para admitir la carga asincrónica también facilita la resolución de los demás problemas siguientes.

### <a name="synchronous-filenetwork-io-requests"></a>Solicitudes sincrónicas de archivos/e/s de red

Idealmente, cualquier solicitud de e/s de red o de archivo sincrónico debe evitarse en el subproceso principal. Su impacto dependerá del estado del equipo y puede bloquearse durante largos períodos de tiempo en algunos casos.

El uso de la carga de paquetes asincrónica y las API de e/s asincrónicas deben asegurarse de que la inicialización del paquete no bloquee el subproceso principal en estos casos. Los usuarios también pueden seguir interactuando con Visual Studio mientras las solicitudes de e/s se producen en segundo plano.

### <a name="early-initialization-of-services-components"></a>Inicialización temprana de servicios, componentes

Uno de los patrones comunes de la inicialización del paquete es inicializar los servicios que usa o proporciona ese paquete en el paquete `constructor` o el `initialize` método. Aunque esto garantiza que los servicios estén listos para usarse, también puede Agregar costos innecesarios a la carga de paquetes si esos servicios no se usan inmediatamente. En su lugar, estos servicios se deben inicializar a petición para minimizar el trabajo realizado en la inicialización del paquete.

En el caso de los servicios globales proporcionados por un paquete, puede utilizar `AddService` métodos que toman una función para inicializar el servicio de forma diferida solo cuando lo solicita un componente. En el caso de los servicios usados en el paquete, puede usar Lazy \<T> o AsyncLazy para asegurarse de \<T> que los servicios se inicializan o se consultan en el primer uso.

## <a name="measuring-impact-of-auto-loaded-extensions-using-activity-log"></a>Medir el impacto de las extensiones cargadas automáticamente mediante el registro de actividad

A partir de Visual Studio 2017 Update 3, el registro de actividad de Visual Studio ahora contendrá entradas para el impacto en el rendimiento de los paquetes durante el inicio y la carga de la solución. Para ver estas medidas, tiene que abrir Visual Studio con el modificador de/log y abrir el archivo de *ActivityLog.xml* .

En el registro de actividad, las entradas estarán en el origen "administrar el rendimiento de Visual Studio" y tendrán un aspecto similar al ejemplo siguiente:

```Component: 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c, Inclusive Cost: 2008.9381, Exclusive Cost: 2008.9381, Top Level Inclusive Cost: 2008.9381```

En este ejemplo se muestra que un paquete con el GUID "3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c" empleó 2008 MS en el inicio de Visual Studio. Tenga en cuenta que Visual Studio considera el costo de nivel superior como el número principal al calcular el impacto de un paquete, ya que sería el ahorro que ven los usuarios al deshabilitar la extensión para ese paquete.

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>Medir el impacto de las extensiones cargadas automáticamente mediante PerfView

Aunque el análisis de código puede ayudar a identificar las rutas de acceso de código que pueden ralentizar la inicialización del paquete, también puede utilizar el seguimiento mediante aplicaciones como PerfView para comprender el impacto de la carga del paquete en el inicio de Visual Studio.

PerfView es una herramienta de seguimiento en todo el sistema. Esta herramienta le ayudará a comprender las rutas de acceso activas en una aplicación, ya sea por el uso de la CPU o el bloqueo de llamadas del sistema. A continuación se muestra un ejemplo rápido sobre cómo analizar una extensión de ejemplo mediante PerfView disponible en el [centro de descarga de Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=28567).

**Código de ejemplo:**

Este ejemplo se basa en el código de ejemplo siguiente, que se ha diseñado para mostrar el caso de algunas causas comunes de retraso:

```csharp
protected override void Initialize()
{
    // Initialize a class from another assembly as an example
    MakeVsSlowServiceImpl service = new MakeVsSlowServiceImpl();

    // Costly work in main thread involving file IO
    string systemPath = Environment.GetFolderPath(Environment.SpecialFolder.Windows);
    foreach (string file in Directory.GetFiles(systemPath))
    {
        DateTime creationDate = File.GetCreationTime(file);
    }

    // Costly work after shell is initialized. This callback executes on main thread
    KnownUIContexts.ShellInitializedContext.WhenActivated(() =>
    {
        DoMoreWork();
    });

    // Start async work on background thread
    DoAsyncWork().Forget();
}

private async Task DoAsyncWork()
{
    // Switch to background thread to do expensive work
    await TaskScheduler.Default;
    System.Threading.Thread.Sleep(500);
}

private void DoMoreWork()
{
    // Costly work
    System.Threading.Thread.Sleep(500);
    // Blocking call to an asynchronous work.
    ThreadHelper.JoinableTaskFactory.Run(async () => { await DoAsyncWork(); });
}
```

**Grabar un seguimiento con PerfView:**

Una vez que haya configurado el entorno de Visual Studio con la extensión instalada, puede grabar un seguimiento del inicio abriendo PerfView y abriendo el cuadro de diálogo **recopilar** en el menú **recopilar** .

![perfview menú recopilar](media/perfview-collect-menu.png)

Las opciones predeterminadas proporcionarán pilas de llamadas para el consumo de CPU, pero como estamos interesados en el tiempo de bloqueo, también debe habilitar las pilas de **tiempo de subproceso** . Una vez que la configuración esté lista, puede hacer clic en **iniciar colección** y, a continuación, abrir Visual Studio después de iniciar la grabación.

Antes de detener la recolección, querrá asegurarse de que Visual Studio está completamente inicializado. la ventana principal es totalmente visible y, si la extensión tiene partes de la interfaz de usuario que se muestran automáticamente, también están visibles. Cuando Visual Studio se haya cargado completamente y se haya inicializado la extensión, puede detener la grabación para analizar el seguimiento.

**Analizar un seguimiento con PerfView:**

Una vez completada la grabación, PerfView abrirá automáticamente el seguimiento y expandirá las opciones.

Para los fines de este ejemplo, estamos interesados principalmente en la vista de **pilas de tiempo de subproceso** que puede encontrar en **grupo avanzado**. Esta vista mostrará el tiempo total invertido en un subproceso por un método, incluidos el tiempo de CPU y el tiempo de bloqueo, como la e/s de disco o la espera en los identificadores.

 ![pilas de tiempo de subprocesos](media/perfview-thread-time-stacks.png)

 Al abrir la vista **pilas de tiempo de subprocesos** , debe elegir el proceso **devenv** para iniciar el análisis.

PerfView tiene instrucciones detalladas sobre cómo leer pilas de tiempo de subproceso bajo su propio menú Ayuda para un análisis más detallado. Para los fines de este ejemplo, deseamos filtrar aún más esta vista incluyendo solo pilas con nuestro nombre de módulo de paquetes y el subproceso de inicio.

1. Establezca **GroupPats** en texto vacío para quitar cualquier agrupación agregada de forma predeterminada.
2. Establezca **IncPats** para incluir parte del nombre del ensamblado y el subproceso de inicio además del filtro de proceso existente. En este caso, debe ser **devenv; Subproceso de inicio; MakeVsSlowExtension**.

Ahora la vista solo mostrará el costo asociado a los ensamblados relacionados con la extensión. En esta vista, las horas que aparecen en la columna **Inc (costo inclusivo)** del subproceso de inicio están relacionadas con nuestra extensión filtrada y afectarán al inicio.

En el ejemplo anterior, algunas pilas de llamadas interesantes serían:

1. E/s con `System.IO` clase: aunque el costo inclusivo de estos marcos podría no ser demasiado caro en el seguimiento, son una causa potencial de un problema, ya que la velocidad de e/s de archivos variará de un equipo a otro.

   ![marcos de e/s del sistema](media/perfview-system-io-frames.png)

2. Llamadas de bloqueo que esperan en otro trabajo asincrónico: en este caso, el tiempo inclusivo representaría la hora en que se bloquea el subproceso principal al finalizar el trabajo asincrónico.

   ![bloquear marcos de llamadas](media/perfview-blocking-call-frames.png)

Una de las otras vistas del seguimiento que serán útiles para determinar el impacto serán las pilas de **carga**de la imagen. Puede aplicar los mismos filtros que se aplican a la vista **pilas de tiempo de subprocesos** y buscar todos los ensamblados cargados debido al código ejecutado por el paquete cargado automáticamente.

Es importante minimizar el número de ensamblados cargados en una rutina de inicialización de paquetes, ya que cada ensamblado adicional implicará una e/s de disco adicional, lo que puede ralentizar el inicio considerablemente en máquinas más lentas.

## <a name="summary"></a>Resumen

El inicio de Visual Studio ha sido una de las áreas en las que se obtienen comentarios continuamente. Nuestro objetivo, tal como se indicó anteriormente, es que todos los usuarios tengan una experiencia de inicio coherente, independientemente de los componentes y las extensiones que hayan instalado. Nos gustaría trabajar con los propietarios de la extensión para ayudarnos a lograr ese objetivo. Las instrucciones anteriores deben ser útiles para comprender el impacto de las extensiones en el inicio y evitar la necesidad de cargarlas automáticamente o cargarlas de forma asincrónica para minimizar el impacto en la productividad de los usuarios.
