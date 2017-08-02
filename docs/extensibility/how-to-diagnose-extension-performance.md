---
title: "Cómo: diagnosticar rendimiento extensión | Documentos de Microsoft"
ms.custom: 
ms.date: 11/08/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
caps.latest.revision: 1
author: BertanAygun
ms.author: bertaygu
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f1226c9bd42476acc9fb57be0a6df8058174fd4d
ms.lasthandoff: 02/22/2017

---
# <a name="measuring-extension-impact-in-startup"></a>Medir el impacto de la extensión en el inicio

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>Centrarse en el rendimiento de la extensión de Visual Studio de 2017

Según los comentarios recibidos, una de las áreas de enfoque de la versión de Visual Studio de 2017 ha sido rendimiento de carga de inicio y la solución. Mientras que el equipo de la plataforma de Visual Studio, hemos estado trabajando para mejorar el rendimiento de carga de inicio y la solución en general, la telemetría sugiere extensiones instaladas también pueden tener una repercusión importante en estos escenarios.

Para ayudar a los usuarios a entender este impacto, hemos agregado una nueva característica de Visual Studio para notificar a los usuarios de extensiones lentas. Cuando Visual Studio detecta una nueva extensión que tiene lenta de inicio o de carga de la solución, los usuarios verán una notificación en el IDE que les dirija al nuevo cuadro de diálogo ""Administrar Visual Studio rendimiento. Este cuadro de diálogo también puede tener acceso al menú de ayuda para buscar extensiones detectadas previamente.

![administrar el rendimiento de Visual Studio](~/docs/extensibility/media/manage-performance.png)

Este documento pretende ayudar a los desarrolladores de extensiones que describen cómo se calcula el impacto de la extensión y cómo pueden analizarse localmente para probar si una extensión puede mostrarse como un rendimiento que afectan a la extensión.

## <a name="how-extensions-can-impact-startup"></a>Cómo pueden afectar a las extensiones de inicio

Una de las maneras más comunes para las extensiones a afectar al rendimiento de inicio es eligiendo la carga automática en uno de los contextos de la interfaz de usuario de inicio conocidos como NoSolutionExists o ShellInitialized. Activar estos contextos de interfaz de usuario durante el inicio y los paquetes que incluyan el atributo "ProvideAutoLoad" en su definición de los contextos, se cargarán y se inicializan en ese momento.

Cuando se mide el impacto de una extensión, nos centramos principalmente en el tiempo invertido por las extensiones que se elija automáticamente la carga en los contextos anteriores. Mide veces incluiría pero no limitarse a:

* Carga de los ensamblados de extensión para los paquetes sincrónico
* Tiempo invertido en el constructor de clase de paquete para paquetes sincrónico
* Tiempo empleado en el método Initialize (o SetSite) de paquete para paquetes sincrónico
* Para paquetes asincrónicos las operaciones anteriores, ejecutan en el subproceso en segundo plano y, por tanto, se excluyen de la supervisión
* Tiempo empleado en el trabajo asincrónico programado durante la inicialización del paquete en el subproceso principal
* Tiempo empleado en los controladores de eventos, específicamente activación de contexto de shell inicializado o el cambio de estado inerte de shell

Hemos agregado varias características a partir de Visual Studio 2015 para ayudar a quitar la necesidad de paquetes de carga automática, posponer la carga a los casos más específicos donde los usuarios sería más seguro que usar la extensión o reducir el impacto de una extensión cuando se cargan automáticamente.

Puede encontrar más detalles acerca de estas características en los siguientes documentos:

[Contextos de la interfaz de usuario basada en reglas](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md): un motor de regla basada más completo creado en torno a contextos de la interfaz de usuario le permiten crear contextos personalizados basados en tipos de proyecto, variantes y capacidades. Estos contextos personalizados pueden utilizarse para cargar un paquete durante los escenarios más específicos, como la presencia de un proyecto con una función específica en lugar de inicio; o permitir [comando visibilidad estarán atados a un contexto personalizado](https://msdn.microsoft.com/en-us/library/bb166512.aspx) basada en funciones del proyecto o en otros términos disponibles, eliminando así la necesidad de cargar un paquete para registrar un controlador de consulta de estado de comando.

[Compatibilidad asincrónica paquetes](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md): la nueva clase base de AsyncPackage en Visual Studio 2015 permite que los paquetes de Visual Studio para cargarse en segundo plano forma asincrónica si se solicitó la carga del paquete mediante un atributo de carga automática o una consulta de servicio asincrónico. Esta carga en segundo plano permite que el IDE a fin de ser capaz de responder mientras se inicializa la extensión en segundo plano y escenarios críticos como carga de inicio y de solución no verse afectados.

[Servicios asincrónicos](how-to-provide-an-asynchronous-visual-studio-service.md): con compatibilidad asincrónica de paquete, también agregó compatibilidad para consultar los servicios de forma asincrónica y poder registrar servicios asincrónicos. Más importante aún, trabajamos de conversión de los servicios de Visual Studio para admitir la consulta asincrónica para que se produzca la mayoría del trabajo en una consulta de async en subprocesos en segundo plano. SComponentModel (host de MEF de Visual Studio) es uno de los servicios principales que admite ahora una consulta asincrónica para permitir las extensiones admitir la carga asincrónica completamente.

## <a name="reducing-impact-of-auto-loaded-extensions"></a>Reducir el impacto de auto extensiones cargadas

Si todavía necesita un paquete se carga al inicio de automáticamente, es importante minimizar el trabajo realizado durante la inicialización de paquete para reducir las posibilidades de la extensión que afectan a inicio.

Algunos ejemplos que podrían provocar la inicialización de paquete costoso son:

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>Uso de la carga del paquete sincrónico en lugar de la carga del paquete asincrónica

Porque los paquetes sincrónico se cargan en el subproceso principal de forma predeterminada, le recomendamos propietario de extensión carga automáticamente los paquetes que utilizan la clase de base de paquete asincrónica en su lugar, como se mencionó anteriormente. Cambiar un paquete de carga automática para admitir cargas asincrónicas también resultará más fácil resolver los problemas siguientes.

### <a name="synchronous-filenetwork-io-requests"></a>Solicitudes de E/S de archivo sincrónicas/red

Lo ideal es que cualquier solicitud de E/S sincrónica de archivos o red debería evitarse en el subproceso principal como su impacto dependerá de estado del equipo y puede bloquear durante largos períodos de tiempo, en algunos casos.

Utilizando la carga asincrónica de paquete y las API de E/S asincrónicas debe asegurarse de que la inicialización del paquete no bloquea el subproceso principal en estos casos y los usuarios puedan interactuar con Visual Studio, mientras que las solicitudes de E/S que se producen en segundo plano.

### <a name="early-initialization-of-services-components"></a>Inicialización temprana de servicios de componentes

Uno de los patrones comunes de inicialización del paquete es inicializar servicios usadas por o proporcionados por ese paquete en el método de constructor o initialize del paquete. Aunque esto garantiza servicios están listos para usarse, también puede agregar costos innecesarios para empaquetar la carga si los servicios no se utilizan inmediatamente. En su lugar, deben inicializar dichos servicios a petición para minimizar el trabajo realizado en la inicialización del paquete.

Para los servicios globales proporcionados por un paquete, puede utilizar los métodos AddService que toma una función para inicializar el servicio de forma diferida sólo cuando se solicita un componente. Para los servicios usados dentro del paquete, puede usar Lazy<T> o AsyncLazy<T> a garantizar servicios inicializado ni consultarse en el primer uso.

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>Medir el impacto de auto carga extensiones mediante PerfView

Aunque el análisis de código puede ayudarle a identificar las rutas de acceso de código que pueden ralentizar la inicialización del paquete, también puede utilizar el seguimiento mediante aplicaciones como PerfView para comprender el impacto de un paquete de carga en el inicio de Visual Studio.

PerfView es una herramienta de seguimiento amplia de sistema que le ayudarán a entender las rutas de acceso activas en una aplicación debido a la CPU o el bloqueo de llamadas del sistema. A continuación se muestra un ejemplo rápido de analizar una extensión de ejemplo mediante PerfView disponible en la [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=28567).

**Código de ejemplo:**

En este ejemplo se basa en el ejemplo de código siguiente, que está diseñado para mostrar algunas causas habituales de retraso de casos:

```c#
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

**Grabación de un seguimiento de PerfView:**

Una vez que configure el entorno de Visual Studio con la extensión instalada, puede grabar una traza de inicio, abra PerfView y cuadro de diálogo recopilar desde el menú "Reunir".

![menú de recopilar perfview](~/docs/extensibility/media/perfview-collect-menu.png)

Las opciones predeterminadas proporcionará las pilas de llamadas para el consumo de CPU, pero puesto que estamos interesados en tiempo de bloqueo, también debe habilitar pilas de "Tiempo de subproceso". Una vez que la configuración esté preparada puede haga clic en "Iniciar colección" e iniciar Visual Studio cuando se inicia la grabación.

Antes de detener la recopilación, desea asegurarse de que Visual Studio está totalmente inicializado, la ventana principal está totalmente visible y si la extensión tiene interfaz de usuario que se muestran automáticamente, también son visibles. Una vez que Visual Studio está completamente cargada y la extensión se ha inicializado, puede detener la grabación para analizar el seguimiento.

**Analizar un seguimiento de PerfView:**

Una vez completada la grabación PerfView será abrir el seguimiento automáticamente y se expanda Opciones.

Para los fines de este ejemplo, estamos interesados principalmente en la vista "De subprocesos de pilas de tiempo" que encontrará en "Advanced Group". Esta vista mostrará el tiempo total invertido en un subproceso por un método incluido el tiempo de CPU y el tiempo de bloqueo, como la E/S de disco o espera en identificadores.

 ![tiempo pilas de subprocesos](~/docs/extensibility/media/perfview-thread-time-stacks.png)

 Al abrir la vista "De subprocesos de pilas de tiempo", debe elegir el proceso "devenv" para iniciar el análisis.

PerfView ha orientación detallada acerca de cómo leer el subproceso pilas de tiempo en su propio menú de ayuda para un análisis más detallado. Para los fines de este ejemplo, deseamos filtrar aún más esta vista solo incluyendo pilas con nuestro subproceso de inicio y el nombre de módulo de paquetes.

1. Establezca "GroupPats" en el texto vacío para quitar cualquier agrupación que se agrega de forma predeterminada.
2. Conjunto "IncPats" para incluir parte de su nombre de ensamblado y el inicio del subproceso además de filtro de proceso existente. En este caso, debe ser "devenv; Subproceso de inicio; MakeVsSlowExtension".

Ahora la vista sólo mostrará el costo asociado con los ensamblados relacionados con la extensión. En esta vista, siempre aparece en la columna "Sa" (costo Inclusive) del subproceso de inicio está relacionada con nuestra extensión filtrado y se pueden influir en el inicio.

Para el ejemplo anterior, algunos interesante llamada pilas sería:

1. E/S usando las clases de System.IO: aunque inclusivo costo de estos marcos no puede ser muy costoso en el seguimiento, son una posible causa de un problema ya que la velocidad de E/S de archivo variará de un equipo a otro.

  ![marcos de e/s del sistema](~/docs/extensibility/media/perfview-system-io-frames.png)

2. Bloqueo de llamadas en espera en otro trabajo asincrónico: en este caso tiempo inclusivo representaría el tiempo que el subproceso principal se bloquea en la finalización del trabajo asincrónico.

  ![marcos de llamada de bloqueo](~/docs/extensibility/media/perfview-blocking-call-frames.png)

Una de las otras vistas de la traza que será útil para determinar el impacto será "Pilas de carga de imagen". Puede aplicar los mismos filtros que se aplican a la vista "De subprocesos de pilas de tiempo" y averiguar todos los ensamblados cargados por el código ejecutado por el paquete de carga automática.

Es importante minimizar el número de ensamblados cargados en una rutina de inicialización de paquete como cada ensamblado adicional implica la E/S de disco adicional que puede ralentizar el inicio considerablemente en equipos más lentos.

## <a name="summary"></a>Resumen

Inicio de Visual Studio ha sido una de las áreas que obtenemos continuamente comentarios en. Nuestro objetivo, como se indicó anteriormente es para que todos los usuarios tengan un inicio coherente experiencia independientemente de los componentes y extensiones que se han instalado y vamos a trabajar con los propietarios de extensión para ayudarles a ayudarnos a alcanzar ese objetivo. Las instrucciones anteriores deben ser útil para comprender el impacto extensiones en el inicio y bien evitando la necesidad de carga de forma automática o cargar asincrónicamente para minimizar el impacto en la productividad del usuario.
