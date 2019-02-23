---
title: Procedimiento Diagnóstico de rendimiento de la extensión | Documentos de Microsoft
ms.date: 11/08/2016
ms.topic: conceptual
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
author: BertanAygun
ms.author: bertaygu
manager: jillfra
ms.workload:
- bertaygu
ms.openlocfilehash: 2d9337b443fdaabe713f1708b2be9051c2f02b3c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56707073"
---
# <a name="measuring-extension-impact-in-startup"></a>Medir el impacto de la extensión de inicio

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>Centrarse en el rendimiento de la extensión en Visual Studio 2017

Según los comentarios recibidos, una de las áreas de enfoque para Visual Studio 2017 versión ha sido rendimiento de carga de inicio y la solución. Como el equipo de plataforma de Visual Studio, hemos estado trabajando en mejorar el rendimiento de carga de inicio y la solución. En general, nuestras mediciones sugieren las extensiones instaladas también pueden tener una repercusión importante en estos escenarios.

Para ayudar a los usuarios a comprender mejor este efecto, hemos agregado una característica nueva en Visual Studio para notificar a los usuarios de las extensiones de baja velocidad. A veces, Visual Studio detecta una nueva extensión que se ralentiza la carga de solución o de inicio. Cuando se detecta una ralentización, los usuarios verán una notificación en el IDE que les dirija al nuevo cuadro de diálogo "Administrar el rendimiento de Visual Studio". Este cuadro de diálogo también siempre se puede acceder al menú Ayuda para buscar extensiones detectadas previamente.

![administrar el rendimiento de Visual Studio](media/manage-performance.png)

El objetivo de este documento es ayudar a los desarrolladores de extensiones con la descripción de cómo se calcula el impacto de la extensión. Este documento también describe cómo se puede analizar el impacto de extensión localmente. Localmente análisis del impacto de la extensión determinará si una extensión se muestren como un rendimiento que afectan a la extensión.

> [!NOTE]
> Este documento se centra en el impacto de las extensiones de carga de inicio y la solución. Las extensiones también afectan el rendimiento de Visual Studio cuando hacen que la interfaz de usuario deje de responder. Para obtener más información sobre este tema, consulte [Cómo: Interfaz de usuario de diagnosticar retrasos causados por las extensiones](how-to-diagnose-ui-delays-caused-by-extensions.md).

## <a name="how-extensions-can-impact-startup"></a>Cómo las extensiones pueden afectar al inicio

Una de las maneras más comunes para las extensiones afectar al rendimiento de inicio es mediante la carga automática en uno de los contextos de interfaz de usuario de inicio conocidos como NoSolutionExists o ShellInitialized. Activar estos contextos de interfaz de usuario durante el inicio. Todos los paquetes que incluyen el `ProvideAutoLoad` atributo en su definición de estos contextos se cargarán y se inicializan en ese momento.

Cuando se mide el impacto de una extensión, nos centramos principalmente en el tiempo invertido por las extensiones que elija para la carga automática en los contextos anteriores. Mide podrían incluir pero no limitarse a veces:

* Carga de ensamblados de extensión para los paquetes sincrónicos
* Tiempo invertido en el constructor de clase de paquete para paquetes sincrónicos
* Tiempo invertido en el método de inicialización (o SetSite) de paquete para los paquetes sincrónicos
* Para paquetes asincrónicos, las operaciones anteriores se ejecutan en el subproceso en segundo plano.  Por lo tanto, las operaciones se excluyen de la supervisión.
* Tiempo invertido en ningún trabajo asincrónico programado durante la inicialización del paquete se ejecute en el subproceso principal
* Tiempo invertido en controladores de eventos, específicamente la activación de contexto shell inicializado o el cambio de estado inerte shell
* A partir de Visual Studio 2017 Update 3, también comenzaremos a supervisar el tiempo invertido en llamadas inactivo antes de inicializa el shell de. Las operaciones largas en inactividad controladores también provocar IDE no responde y contribuyen al tiempo de inicio percibido por el usuario.

Hemos agregado muchas características a partir de Visual Studio 2015. Estas características ayudan con la eliminación de la necesidad de paquetes de carga automático. Las características también posponer la necesidad de paquetes para cargar los casos más específicas. Estos casos incluyen ejemplos donde los usuarios podrían más determinados usar la extensión o reducir el impacto de una extensión cuando se cargan automáticamente.

Puede encontrar más detalles sobre estas características en los siguientes documentos:

[Contextos de interfaz de usuario basada en reglas](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md): Un motor más completo de están basadas en reglas creado en torno a los contextos de interfaz de usuario permite crear contextos personalizados basadas en atributos, tipos y tipos de proyecto. Contextos personalizados pueden utilizarse para cargar un paquete durante escenarios más específicos. Estos escenarios específicos incluyen la presencia de un proyecto con una función específica en lugar de inicio. También permiten contextos personalizados [comando visibilidad esté vinculada a un contexto personalizado](visibilityconstraints-element.md) en función de los componentes del proyecto u otros términos disponibles. Esta característica elimina la necesidad de cargar un paquete para registrar un controlador de consulta de estado de comandos.

[Compatibilidad con paquetes asincrónica](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md): La nueva clase de base de AsyncPackage en Visual Studio 2015 permite que los paquetes de Visual Studio que se cargue en segundo plano forma asincrónica si se solicitó la carga del paquete mediante un atributo de la carga automática o una consulta de servicio asincrónico. Esta carga en segundo plano permite que el IDE a fin de responder. El IDE está respondiendo incluso mientras se inicializa la extensión en segundo plano y no se verá afectados escenarios críticos, como la carga de inicio y la solución.

[Servicios asincrónicos](how-to-provide-an-asynchronous-visual-studio-service.md): Con compatibilidad asincrónica de paquete, también hemos agregado compatibilidad para consultar los servicios de forma asincrónica y poder registrar los servicios asincrónicos. Más importante aún estamos trabajando de conversión de los servicios de Visual Studio principales para admitir la consulta asincrónica para que se produzca la mayoría del trabajo en una consulta de async en subprocesos en segundo plano. SComponentModel (host de MEF de Visual Studio) es uno de los servicios principales que ahora es compatible con una consulta asincrónica para permitir las extensiones admitir la carga asincrónica por completo.

## <a name="reducing-impact-of-auto-loaded-extensions"></a>Reducir el impacto de auto extensiones cargadas

Si todavía necesita un paquete se carga al inicio de automáticamente, es importante minimizar el trabajo realizado durante la inicialización del paquete. Minimizar el trabajo de inicialización del paquete reduce las posibilidades de la extensión que afectan a inicio.

Algunos ejemplos que podrían provocar que la inicialización costoso paquete son:

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>Uso de la carga del paquete sincrónico en lugar de la carga del paquete asincrónica

Porque los paquetes sincrónicos se cargan en el subproceso principal de forma predeterminada, le animamos a los propietarios de extensión que tienen paquetes de carga automáticamente para usar la clase base paquete asincrónica en su lugar como se mencionó anteriormente. Cambiar un paquete de carga automática para admitir cargas asincrónicas también resultará más fácil de resolver los problemas siguientes.

### <a name="synchronous-filenetwork-io-requests"></a>Solicitudes de E/S de archivo sincrónicas/red

Lo ideal es que se debe evitar cualquier solicitud de E/S de archivos o red sincrónico en el subproceso principal. Su impacto dependerá de estado de la máquina y se puede bloquear durante largos períodos de tiempo en algunos casos.

Utilizando la carga del paquete asincrónica y las API de E/S asincrónicas debe asegurarse que la inicialización del paquete no bloquea el subproceso principal en estos casos. Los usuarios también pueden continuar interactuar con Visual Studio, mientras que las solicitudes de E/S que se producen en segundo plano.

### <a name="early-initialization-of-services-components"></a>Inicialización temprana de servicios, componentes

Uno de los patrones comunes de inicialización del paquete consiste en inicializar los servicios proporcionados por ese paquete en el paquete o utilizado por `constructor` o `initialize` método. Aunque esto garantiza que los servicios están listos para usarse, también puede agregar costos innecesarios para empaquetar la carga si esos servicios no se utilizan inmediatamente. En su lugar se deben inicializar dichos servicios a petición para minimizar el trabajo realizado en la inicialización del paquete.

Proporcionado por un paquete de servicios globales, puede usar `AddService` métodos que toman una función para inicializar el servicio de forma diferida solo cuando se solicita un componente. Para los servicios utilizados dentro del paquete, puede usar Lazy<T> o elemento AsyncLazy<T> para asegurarse de que los servicios son inicializado ni consultarse en el primer uso.

## <a name="measuring-impact-of-auto-loaded-extensions-using-activity-log"></a>Medición del impacto de auto carga extensiones mediante el registro de actividad

A partir de Visual Studio 2017 Update 3, registro de actividad de Visual Studio ahora contendrá las entradas de impacto en el rendimiento de los paquetes durante la carga de inicio y la solución. Para ver estas mediciones, tiene que iniciar Visual Studio con el modificador/log y abra *ActivityLog.xml* archivo.

En el registro de actividad, las entradas se encontrarán en el origen de "Administrar el rendimiento de Visual Studio" y tendrá un aspecto similar al ejemplo siguiente:

```Component: 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c, Inclusive Cost: 2008.9381, Exclusive Cost: 2008.9381, Top Level Inclusive Cost: 2008.9381```

En este ejemplo muestra que un paquete con el GUID "3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c" dedicado a 2008 ms en el inicio de Visual Studio. Tenga en cuenta que Visual Studio tiene en cuenta el costo de nivel superior como el número principal al calcular el impacto de un paquete, ya que sería que verán los usuarios de ahorro cuando deshabilita la extensión de ese paquete.

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>Medición del impacto de auto carga extensiones mediante PerfView

Mientras el análisis de código puede ayudar a identificar las rutas de código que pueden ralentizar la inicialización del paquete, también puede utilizar el seguimiento mediante el uso de aplicaciones como PerfView para comprender el impacto de un paquete de carga en el inicio de Visual Studio.

PerfView es una herramienta de seguimiento de todo el sistema. Esta herramienta le ayudará a comprender las rutas de acceso activas en una aplicación, ya sea debido a uso de CPU o bloquear las llamadas del sistema. A continuación es un ejemplo rápido acerca de cómo analizar una extensión de ejemplo con PerfView disponible en el [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=28567).

**Ejemplo de código:**

En este ejemplo se basa en el ejemplo de código siguiente, que está diseñado para mostrar algunas causas comunes de retraso de casos:

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

**Grabación de un objeto trace con PerfView:**

Una vez configurado el entorno de Visual Studio con la extensión instalada, puede registrar un seguimiento del inicio, abra PerfView y abra el **recopilar** cuadro de diálogo desde el **recopilar** menú.

![menú recopilar perfview](media/perfview-collect-menu.png)

Las opciones predeterminadas proporcionará las pilas de llamadas para el consumo de CPU, pero puesto que estamos interesados en tiempo de bloqueo, también debe habilitar **tiempo subprocesos** pilas. Una vez que la configuración esté lista, puede hacer clic en **iniciar colección** e iniciar Visual Studio una vez que se inicia la grabación.

Antes de detener la recopilación, desea asegurarse de que Visual Studio está completamente inicializado, la ventana principal está completamente visible y si la extensión tiene interfaz de usuario que se muestran automáticamente, también están visibles. Una vez que Visual Studio se cargó completamente y se inicializa la extensión, puede detener la grabación para analizar el seguimiento.

**Analizar un seguimiento con PerfView:**

Una vez completada la grabación de PerfView automáticamente se abra el seguimiento y expanda las opciones.

Para los fines de este ejemplo, nos interesa principalmente la **las pilas de subprocesos en tiempo** vista que puede encontrar en **Advanced Group**. Esta vista mostrará el tiempo total invertido en un subproceso por un método como el tiempo de CPU y tiempo de bloqueo, como E/S de disco o en espera en identificadores.

 ![tiempo pilas de subprocesos](media/perfview-thread-time-stacks.png)

 Mientras se abre **las pilas de subprocesos en tiempo** ver, debe elegir el **devenv** proceso para iniciar el análisis.

PerfView ha orientación detallada acerca de cómo se leen las pilas en tiempo en su propio menú de ayuda para un análisis más detallado de subproceso. Para fines de este ejemplo, desea filtrar aún más esta vista solo incluyendo pilas con el subproceso de inicio y el nombre de módulo de paquetes.

1. Establecer **GroupPats** en texto vacío para quitar cualquier agrupación que se agrega de forma predeterminada.
2. Establecer **IncPats** para incluir parte de su nombre de ensamblado y el inicio del subproceso además de filtro de proceso existente. En este caso, debe ser **devenv; Subproceso de inicio; MakeVsSlowExtension**.

Ahora la vista solo mostrará el costo asociado con los ensamblados relacionados con la extensión. En esta vista, siempre que se muestra bajo el **Inc (costo inclusivo)** columna del subproceso de inicio se relaciona con nuestra extensión filtrado y se pueden influir en el inicio.

Para el ejemplo anterior, algunos interesante llamada pilas sería:

1. Uso de E/S `System.IO` clase: Aunque inclusivo costo de estos marcos podría no ser demasiado costosa en el seguimiento, son una posible causa de un problema ya que la velocidad de E/S de archivos puede variar de un equipo a otro.

   ![marcos de e/s del sistema](media/perfview-system-io-frames.png)

2. Bloqueo de las llamadas a la espera en otro trabajo asincrónico: En este caso, el tiempo inclusivo representaría el tiempo que se bloquea el subproceso principal tras la finalización del trabajo asincrónico.

   ![marcos de llamada de bloqueo](media/perfview-blocking-call-frames.png)

Una de las otras vistas en el seguimiento que resultarán útiles para conocer el impacto será el **pilas de carga de imágenes**. Puede aplicar los mismos filtros que se aplican a **las pilas de subprocesos en tiempo** ver y averiguar todos los ensamblados cargados por el código ejecutado por el paquete cargado automáticamente.

Es importante minimizar el número de ensamblados cargados dentro de una rutina de inicialización del paquete como cada ensamblado adicional implicará la E/S de disco adicional que puede ralentizar el inicio considerablemente en equipos más lentos.

## <a name="summary"></a>Resumen

Inicio de Visual Studio ha sido una de las áreas en que continuamente recibimos comentarios. Nuestro objetivo, como se indicó anteriormente es para que todos los usuarios tengan un inicio coherente experiencia independientemente de los componentes y extensiones que han instalado. Nos gustaría trabajar con los propietarios de extensión que les ayuden a alcanzar ese objetivo. Las instrucciones anteriores deben ser útil para comprender un impacto de las extensiones en el inicio y o evitar la necesidad de auto carga o cargarlo de forma asincrónica para minimizar el impacto en la productividad del usuario.
