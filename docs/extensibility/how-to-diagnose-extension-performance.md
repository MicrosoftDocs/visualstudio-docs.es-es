---
title: "Cómo: diagnosticar el rendimiento de la extensión | Documentos de Microsoft"
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: b78a02b9d780b9556cbbf42fce04b1da06e22833
ms.contentlocale: es-es
ms.lasthandoff: 09/26/2017

---
# <a name="measuring-extension-impact-in-startup"></a>Medir el impacto de la extensión de inicio

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>Céntrese en el rendimiento de la extensión en Visual Studio de 2017

Según los comentarios del cliente, una de las áreas de enfoque para la versión de Visual Studio de 2017 ha sido inicio y solución de rendimiento de carga. Mientras que, como equipo de la plataforma de Visual Studio, hemos estado trabajando para mejorar el rendimiento de carga de inicio y la solución en general, la telemetría sugiere las extensiones instaladas también pueden tener una repercusión importante en estos escenarios.

Para ayudar a los usuarios a comprender mejor este efecto, hemos agregado una característica nueva en Visual Studio para notificar a los usuarios de las extensiones de baja velocidad. Cuando Visual Studio detecta una nueva extensión que se ralentice de carga de la solución o inicio, los usuarios verán una notificación en el IDE que se dirijan al nuevo cuadro de diálogo "Administrar del rendimiento de Visual Studio". Este cuadro de diálogo también puede tener acceso al menú de ayuda para buscar extensiones detectadas previamente.

![administrar el rendimiento de Visual Studio](media/manage-performance.png)

Este documento tiene como objetivo ayudar a los desarrolladores de extensión, se describen cómo se calcula el impacto de la extensión y cómo puede analizarse localmente para probar si una extensión puede mostrarse como un rendimiento que afectan a la extensión.

## <a name="how-extensions-can-impact-startup"></a>Cómo pueden afectar a las extensiones de inicio

Uno de los usos más comunes de extensiones que se va a afectar al rendimiento de inicio es mediante la selección automática de carga en uno de los contextos de la interfaz de usuario de inicio conocidos como NoSolutionExists o ShellInitialized. Activar estos contextos de interfaz de usuario durante el inicio y todos los paquetes que incluyan el atributo "ProvideAutoLoad" en su definición con estos contextos se cargarán y se inicializan en ese momento.

Cuando se miden el impacto de una extensión, se centra principalmente en el tiempo invertido por las extensiones que decide carga automáticamente en los contextos anteriores. Mide veces incluiría pero no limitarse a:

* Carga de ensamblados de extensión para los paquetes sincrónicos
* Tiempo invertido en el constructor de clase de paquete para paquetes sincrónicos
* Tiempo empleado en el método de inicialización (o SetSite) de paquete para paquetes sincrónicos
* Para los paquetes asincrónicos las operaciones anteriores, ejecutan en el subproceso en segundo plano y, por tanto, se excluyen de la supervisión
* Tiempo empleado en cualquier trabajo asincrónico programado durante la inicialización de paquete para ejecutarse en el subproceso principal
* Tiempo invertido en controladores de eventos, concretamente activación de contexto de shell inicializado o el cambio de estado inerte de shell
* A partir de Visual Studio de 2017 Update 3, también Empezaremos tiempo empleado en llamadas inactivo antes de inicializa el shell de supervisión. Operaciones de larga duración en los controladores de inactividad también provocar IDE no responde y contribuyan a la hora de inicio percibido por el usuario.

Hemos agregado varias funciones a partir de Visual Studio 2015 para ayudar a quitar la necesidad de paquetes para la carga automática, posponer su carga a los casos más específicos donde los usuarios sería más seguro que usar la extensión o reducir el impacto de una extensión al cargar de forma automática.

Puede encontrar más detalles acerca de estas características en los siguientes documentos:

[Contextos de interfaz de usuario basada en reglas](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md): un motor basada en reglas más completo creado en torno a los contextos de interfaz de usuario le permiten crear contextos personalizadas basadas en tipos de proyecto, tipos y funciones. Estos contextos personalizados pueden utilizarse para cargar un paquete durante situaciones más específicos, como la presencia de un proyecto con una función específica en lugar de inicio; o permitir [comando visibilidad vincular a un contexto personalizado](https://msdn.microsoft.com/en-us/library/bb166512.aspx) en función de las capacidades de proyectos u otros términos disponibles, por tanto, lo que elimina la necesidad de cargar un paquete para registrar un controlador de consulta de estado de comando.

[Compatibilidad con paquetes asincrónica](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md): la nueva clase de base de AsyncPackage en Visual Studio 2015 permite que los paquetes de Visual Studio para cargarse en segundo plano forma asincrónica si se solicitó la carga del paquete mediante un atributo de la carga automática o una consulta de servicio asincrónicos . Esta carga en segundo plano permite que el IDE para ser capaz de responder mientras se inicializa la extensión en segundo plano y no verse afectados escenarios críticos, como carga de inicio y la solución.

[Servicios asincrónicos](how-to-provide-an-asynchronous-visual-studio-service.md): con la compatibilidad asincrónica paquete, también hemos agregado compatibilidad para consultar los servicios de forma asincrónica y poder registrar servicios asincrónicos. Lo más importante es que estamos trabajando sobre la conversión de servicios de Visual Studio principales para admitir la consulta asincrónica para que la mayor parte del trabajo en una consulta asincrónica tiene lugar en subprocesos en segundo plano. SComponentModel (host de MEF de Visual Studio) es uno de los servicios principales que ahora es compatible con una consulta asincrónica para permitir las extensiones admitir completamente la carga asincrónica.

## <a name="reducing-impact-of-auto-loaded-extensions"></a>Reducir el impacto de "auto" extensiones cargadas

Si todavía necesita un paquete se carga al inicio de automáticamente, es importante minimizar el trabajo realizado durante la inicialización de paquete para reducir las posibilidades de la extensión afectando al inicio.

Algunos ejemplos que pudieron provocar la inicialización de paquete ser costoso son:

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>Uso de la carga del paquete sincrónico en lugar de la carga del paquete asincrónica

Porque paquetes sincrónicos se cargan en el subproceso principal de forma predeterminada, le animamos a los propietarios de extensión que tienen automática cargar paquetes usan la clase base paquete asincrónica en su lugar, como se mencionó anteriormente. Cambiar un paquete de carga automática para admitir la carga asincrónica también resultará más fácil resolver los problemas siguientes.

### <a name="synchronous-filenetwork-io-requests"></a>Solicitudes de E/S de archivo/red sincrónico

Lo ideal es que cualquier solicitud de E/S de archivo o red sincrónica debería evitarse en el subproceso principal como su impacto dependerá de estado de la máquina y se puede bloquear durante largos períodos de tiempo en algunos casos.

Uso de carga del paquete asincrónica y las API de E/S asincrónicas debe asegurarse de que la inicialización de paquete no bloquea el subproceso principal en estos casos y los usuarios pueden seguir interactuar con Visual Studio, mientras que las solicitudes de E/S que se producen en segundo plano.

### <a name="early-initialization-of-services-components"></a>Inicialización temprana de servicios, componentes

Uno de los patrones comunes de inicialización de paquete consiste en inicializar servicios utilizados por o proporcionados por ese paquete en el método de inicialización o el constructor del paquete. Aunque esto garantiza que los servicios están listos para ser utilizadas, también puede agregar costos innecesarios para empaquetar se carguen si esos servicios no se utilizan inmediatamente. En su lugar deben inicializarse dichos servicios a petición para minimizar el trabajo realizado en la inicialización de paquete.

Para los servicios globales proporcionados por un paquete, puede usar los métodos de AddService que toma una función para inicializar el servicio de forma diferida solo cuando se solicita un componente. Para obtener servicios que se utilizan dentro del paquete, puede usar Lazy<T> o AsyncLazy<T> para asegurarse de que los servicios están inicializado ni consultarse por primera vez.

## <a name="measuring-impact-of-auto-loaded-extensions-using-activity-log"></a>Medir el impacto de "auto" carga extensiones mediante el registro de actividad

A partir de Visual Studio de 2017 Update 3, registro de actividad de Visual Studio ahora contiene entradas para el impacto de rendimiento de los paquetes durante la carga de inicio y la solución. Para ver estas medidas, tendrá que iniciar Visual Studio con el modificador/log y abra el archivo ActivityLog.xml.

En el registro de actividad, las entradas estarán en el origen de "Administrar del rendimiento de Visual Studio" y tendrá un aspecto similar a siguiente:

```Component: 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c, Inclusive Cost: 2008.9381, Exclusive Cost: 2008.9381, Top Level Inclusive Cost: 2008.9381```

Esto significa que el paquete con GUID "3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c" empleado ms 2008 en el inicio de Visual Studio. Tenga en cuenta que Visual Studio tiene en cuenta los costos de nivel superior como el número principal al calcular el impacto de un paquete como sería el usuario savigs vea cuando deshabilita la extensión de ese paquete.

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>Medir el impacto de "auto" carga extensiones mediante PerfView

Mientras que el análisis de código pueden ayudar a identificar las rutas de código que pueden ralentizar la inicialización de paquete, también puede usar el seguimiento mediante el uso de aplicaciones como PerfView para entender el impacto de un paquete de carga en el inicio de Visual Studio.

PerfView es una herramienta de seguimiento ancho de sistema que le ayudará a comprender las rutas de acceso activas en una aplicación, ya sea debido al uso de CPU o el bloqueo de llamadas del sistema. A continuación se muestra un ejemplo rápido acerca de cómo analizar una extensión de ejemplo mediante PerfView disponible en la [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=28567).

**Código de ejemplo:**

En este ejemplo se basa en el ejemplo de código siguiente, que está diseñada para mostrar caso algunas causas habituales de retraso:

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

**Grabación de un seguimiento con PerfView:**

Una vez que configure el entorno de Visual Studio con la extensión instalada, puede registrar un seguimiento del proceso de inicio, abra PerfView y abrir el diálogo recopilar desde el menú "Recopilar".

![menú recopilar perfview](media/perfview-collect-menu.png)

Las opciones predeterminadas proporcionará las pilas de llamadas para el consumo de CPU, pero puesto que estamos interesados en tiempo de bloqueo, también debe habilitar pilas de "Tiempo de subproceso". Una vez que la configuración esté lista puede hacer clic en "Iniciar colección" e iniciar Visual Studio una vez que se inicia la grabación.

Antes de detener la recopilación, desea asegurarse de que Visual Studio está totalmente inicializado, la ventana principal está completamente visible y si la extensión tiene cualquier partes de la interfaz de usuario que se muestran automáticamente, también están visibles. Una vez que Visual Studio está completamente cargada y la extensión se inicializa, puede detener la grabación para analizar el seguimiento.

**Analizar un seguimiento con PerfView:**

Una vez completada la grabación de PerfView automáticamente se abra el seguimiento y expanda las opciones.

Para los fines de este ejemplo, nos interesa principalmente en la vista "De subprocesos de pilas de tiempo" que encontrará en "Advanced Group". Esta vista mostrará el tiempo total invertido en un subproceso por un método como el tiempo de CPU y tiempo de bloqueo, como E/S de disco o esperando en identificadores.

 ![tiempo pilas de subprocesos](media/perfview-thread-time-stacks.png)

 Al abrir la vista "De subprocesos de pilas de tiempo", debe elegir el proceso de "devenv" para iniciar el análisis.

PerfView, detallaron instrucciones sobre cómo leer subproceso pilas de tiempo en su propio menú de ayuda para un análisis más detallado. Para fines de este ejemplo, desea filtrar aún más esta vista solo incluyendo pilas con nuestro subproceso de inicio y el nombre de módulo de paquetes.

1. Establezca "GroupPats" en el texto vacío para quitar cualquier agrupación agregada de forma predeterminada.
2. Conjunto "IncPats" para incluir parte de su nombre de ensamblado y el inicio del subproceso además de filtro de proceso existente. En este caso, debe ser "devenv; Subproceso de inicio; MakeVsSlowExtension".

Ahora la vista solo mostrará el costo asociado con los ensamblados relacionados con la extensión. En esta vista, siempre que aparecen en la columna "Sa" (costo Inclusive) del subproceso de inicio está relacionado con la extensión de filtrado y se pueden influir en el inicio.

Para el ejemplo anterior, algunos llamada interesante pilas sería:

1. E/S usando la clase de System.IO: al costo inclusivo de estos marcos podría no ser costosa en el seguimiento, son una posible causa de un problema ya que la velocidad de E/S de archivo variará de un equipo a otro.

  ![marcos de e/s del sistema](media/perfview-system-io-frames.png)

2. Llamadas en espera en otro trabajo asincrónico de bloqueo: en este caso de tiempo inclusivo representaría el tiempo que se bloquea el subproceso principal en la finalización del trabajo asincrónico.

  ![marcos de llamada de bloqueo](media/perfview-blocking-call-frames.png)

Una de las otras vistas en el seguimiento que le serán útiles para conocer el impacto será "Pilas de carga de imagen". Puede aplicar los mismos filtros tal como se aplica a la vista "De subprocesos de pilas de tiempo" y averiguar todos los ensamblados cargados por el código ejecutado por el paquete cargado automáticamente.

Es importante minimizar el número de ensamblados cargados dentro de una rutina de inicialización de paquete como cada ensamblado adicional implicará la E/S de disco adicional que puede ralentizar el inicio considerablemente en equipos más lentos.

## <a name="summary"></a>Resumen

Inicio de Visual Studio ha sido una de las áreas que obtenemos continuamente comentarios en. Nuestro objetivo como se mencionó anteriormente es para que todos los usuarios que tienen un inicio coherente experiencia independientemente de los componentes y extensiones que se han instalado y nos gustaría trabajar con los propietarios de extensión para ayudarles a nos ayudan a lograr este objetivo. Las instrucciones anteriores deben ser útil para comprender un impacto de las extensiones en el inicio y o evitar la necesidad de automáticamente la carga o cargar de forma asincrónica para minimizar el impacto en la productividad del usuario.

