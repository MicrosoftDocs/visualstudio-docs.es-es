---
title: "Administrar la carga de proyecto en una soluci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "soluciones, administrar la carga del proyecto"
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# Administrar la carga de proyecto en una soluci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Soluciones de Visual Studio pueden contener un gran número de proyectos. El comportamiento de Visual Studio de forma predeterminada es cargar todos los proyectos de una solución en el momento en que se abra la solución y no se permite al usuario tener acceso a cualquiera de los proyectos hasta que todos ellos han terminado de cargarse. Cuando el proceso de carga del proyecto durará más de dos minutos, se muestra una barra de progreso que muestra el número de proyectos que se carga y el número total de proyectos. El usuario puede descargar los proyectos mientras trabaja en una solución con varios proyectos, pero este procedimiento tiene algunas desventajas: no se compilan los proyectos de descargados como parte de un comando de volver a generar solución y no se muestran las descripciones de IntelliSense de tipos y miembros de proyectos cerrados.  
  
 Los desarrolladores pueden reducir los tiempos de carga de la solución y administrar el comportamiento de carga mediante la creación de una carga de solución Administrador de proyecto. El Administrador de carga de la solución puede establecer otro proyecto cargar prioridades para proyectos específicos o tipos de proyecto, asegúrese de que los proyectos se cargan antes de iniciar una compilación de fondo, retrasar la carga de segundo plano hasta que se completen otras tareas en segundo plano y realizar otras tareas de administración de carga de proyecto.  
  
## Cargando las prioridades del proyecto  
 Visual Studio define cuatro prioridades de carga de proyecto diferente:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority> \(valor predeterminado\): cuando se abre una solución, los proyectos se cargan de forma asincrónica. Si esta prioridad se establece en un proyecto sin cargar después de que la solución ya está abierta, el proyecto se cargará en el siguiente punto inactivo.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: cuando se abre una solución, los proyectos se cargan en segundo plano, que permite al usuario tener acceso a los proyectos que se cargan sin tener que esperar hasta que se cargan todos los proyectos.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: los proyectos se cargan cuando se tiene acceso. Se tiene acceso a un proyecto cuando el usuario expande el nodo del proyecto en el Explorador de soluciones cuando se abre un archivo de proyecto cuando se abre la solución porque está en la lista de documentos abiertos \(guardada en el archivo de opciones de usuario de la solución\), o cuando otro proyecto que se está cargando tiene una dependencia en el proyecto. Este tipo de proyecto no se carga automáticamente antes de iniciar un proceso de compilación; el Administrador de carga de la solución es responsable de garantizar que todos los proyectos necesarios están cargados. Estos proyectos también se deben cargar antes de iniciar una buscar y reemplazar en archivos en toda la solución.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: los proyectos no tienen que cargarse a menos que el usuario lo solicita explícitamente. Esto sucede cuando los proyectos se descargan de forma explícita.  
  
## Creación de una carga de solución administrador  
 Los desarrolladores pueden crear una carga de solución manager implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> y aconsejar a Visual Studio que el Administrador de carga de la solución está activo.  
  
#### Activación de un administrador de carga de la solución  
 Visual Studio permite a sólo un administrador de solución de carga en un momento dado, por lo que deberá notificar Visual Studio si desea activar la carga de la solución manager. Si un administrador de carga segunda solución está activado más adelante, se desconectará el Administrador de carga de la solución.  
  
 Debe obtener el <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> de servicio y establezca el <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> propiedad:  
  
```c#  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution; object objLoadMgr = this;   //the class that implements IVsSolutionManager pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### Implementación IVsSolutionLoadManager  
 El <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A> se invoca durante el proceso de apertura de la solución. Para implementar este método, utiliza el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport> servicio para establecer la prioridad de carga para el tipo de proyecto que desea administrar. Por ejemplo, el siguiente código establece tipos de proyectos de C\# para cargar en segundo plano:  
  
```c#  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}"); pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 El <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> se invoca cuando se cierra Visual Studio o cuando un paquete diferente ha asumido como el Administrador de carga de la solución activa llamando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> con el <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> propiedad.  
  
#### Estrategias para distintos tipos de administrador de carga de la solución  
 Puede implementar administradores de carga de solución de maneras diferentes, dependiendo de los tipos de soluciones que están diseñadas para administrar.  
  
 Si el Administrador de carga de la solución se ha diseñado para administrar la solución de carga en general, se puede implementar como parte de un paquete VSPackage. El paquete se debe establecer en autoload agregando el <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> en el paquete VSPackage con un valor de <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>. A continuación, se puede activar el Administrador de carga de la solución en el <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> \(método\).  
  
> [!NOTE]
>  Para obtener más información acerca de los paquetes de carga automática, consulte [Cargar VSPackages](../extensibility/loading-vspackages.md).  
  
 Dado que Visual Studio reconoce solo la última solución carga manager activarse, administradores de carga de la solución general siempre deberían detectar si hay un administrador de carga antes de activar a sí mismos. Si una llamada a GetProperty\(\) en el servicio de solución de <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> devuelve `null`, no hay ningún administrador de carga de la solución activa. Si no devuelve null, compruebe si el objeto es el mismo que el Administrador de carga de la solución.  
  
 Si el Administrador de carga de la solución se ha diseñado para administrar solo unos pocos tipos de soluciones, el paquete VSPackage puede suscribirse a eventos de carga de la solución \(mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>\) y utilizar el controlador de eventos <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> para activar el Administrador de carga de la solución.  
  
 Si el Administrador de carga de la solución se ha diseñado para administrar sólo soluciones específicas, la información de activación puede conservarse como parte del archivo de solución. Para ello, llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> para la sección solución anterior.  
  
 Los administradores de carga de solución específica deben desactivar a sí mismos en la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> el controlador de eventos, para que no entre en conflicto con otros administradores de carga de la solución.  
  
 Si necesita un administrador de carga de la solución sólo para conservar las prioridades de carga global del proyecto \(por ejemplo, se establecen en una página de opciones\), puede activar el Administrador de carga de la solución en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> el controlador de eventos, conservar la configuración de las propiedades de la solución y desactivar el Administrador de carga de la solución.  
  
## Control de eventos de carga de solución  
 Para suscribirse a eventos de carga de la solución, llamada <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> al activar el Administrador de carga de la solución. Si implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, puede responder a eventos relacionados con las prioridades de la carga de proyecto diferente.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Esto se desencadena antes de que se abre una solución. Puede utilizarlo para cambiar el proyecto de prioridad para los proyectos de la solución de carga.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Se desencadena después de que la solución esté completamente cargada, pero antes de fondo proyecto carga comienza de nuevo. Por ejemplo, un usuario podría haber accedido a un proyecto cuya prioridad de carga es LoadIfNeeded o el Administrador de carga de la solución puede haber cambiado una prioridad de carga del proyecto a BackgroundLoad, que podría iniciar una carga en segundo plano de ese proyecto.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Se desencadena después de carga inicialmente totalmente una solución, haya o no un administrador de carga de la solución. También se activa después de carga en segundo plano o petición carga siempre que la solución se ha cargado completamente. Al mismo tiempo, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> se reactiva.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Esto se activa antes de la carga de un proyecto \(o proyectos\). Para asegurarse de que otros procesos en segundo plano se completan antes de que los proyectos se carguen, establezca `pfShouldDelayLoadToNextIdle` a **true**.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Se desencadena cuando un lote de proyectos está a punto de cargarse. Si `fIsBackgroundIdleBatch` es true, los proyectos son carga en segundo plano; si `fIsBackgroundIdleBatch` es false, los proyectos que van a cargarse sincrónicamente como resultado de una solicitud del usuario, por ejemplo si el usuario expande un proyecto pendiente en el Explorador de soluciones. Puede implementar para realizar un trabajo costoso que de lo contrario tendría que hacerse en <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterOpenProject%2A>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Se desencadena después de que se ha cargado un lote de proyectos.  
  
## Detectar y administrar soluciones y la carga del proyecto  
 Para detectar el estado de carga de los proyectos y soluciones, llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> con los valores siguientes:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` devuelve `true` Si la solución y todos sus proyectos están cargados, de lo contrario, `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` devuelve `true` Si un lote de proyectos están cargadas actualmente en segundo plano, de lo contrario, `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` devuelve `true` Si un lote de proyectos actualmente se cargan sincrónicamente como resultado de un comando de usuario u otra carga explícita, de lo contrario, `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` devuelve `true` Si la solución está actualmente está cerrada, de lo contrario, `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` devuelve `true` Si una solución está actualmente está abierta, en caso contrario `false`.  
  
 También puede asegurarse de que se cargan los proyectos y soluciones \(sin importar cuáles sean las prioridades de carga del proyecto\) llamando a uno de los métodos siguientes:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: llamar a este método obliga a los proyectos en una solución de carga antes de que el método devuelve.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: llamar a este método obliga a los proyectos de `guidProject` cargar antes de que el método devuelve.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: este método obliga el proyecto en `guidProjectID` cargar antes de que el método devuelve.  
  
> [!NOTE]
>  . De forma predeterminada sólo los proyectos que tienen la demanda de cargan y se cargan las prioridades de carga de segundo plano, pero si el <xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS> marca se pasa al método, se cargarán todos los proyectos excepto las que se marcan para cargar explícitamente.