---
title: "Administrar la carga del proyecto en una solución | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a2be2c75704646bab50f89377d960d44f6fa14f1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="managing-project-loading-in-a-solution"></a>Administrar la carga de proyecto en una solución
Soluciones de Visual Studio pueden contener un gran número de proyectos. El comportamiento predeterminado de Visual Studio es cargar todos los proyectos en una solución en el momento en que se abre la solución y no permite al usuario tener acceso a cualquiera de los proyectos hasta que todas ellas han terminado de cargarse. Cuando el proceso de carga de proyecto durará más de dos minutos, se muestra una barra de progreso que muestra el número de proyectos cargados y el número total de proyectos. El usuario puede descargar proyectos mientras trabaja en una solución con varios proyectos, pero este procedimiento tiene algunas desventajas: no se compilan los proyectos de descargados como parte de un comando de volver a generar solución, y las descripciones de IntelliSense de tipos y miembros de cerrado no se muestran los proyectos.  
  
 Los desarrolladores pueden reducir los tiempos de carga de solución y administrar el comportamiento de carga mediante la creación de una carga de la solución el administrador del proyecto. Puede establecer otro proyecto cargar las prioridades para los proyectos específicos o tipos de proyecto, asegúrese de que los proyectos se cargan antes de iniciar una compilación de fondo, retrasar la carga de fondo hasta que finalicen otras tareas en segundo plano y realizar el Administrador de carga de la solución otras tareas de administración de carga de proyecto.  
  
## <a name="project-loading-priorities"></a>Cargar las prioridades del proyecto  
 Visual Studio define cuatro prioridades de carga de proyecto diferente:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>(el valor predeterminado): cuando se abre una solución, los proyectos se cargan de forma asincrónica. Si esta prioridad se establece en un proyecto sin cargar después de que la solución ya está abierta, el proyecto se cargará en el siguiente punto inactivo.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: cuando se abre una solución, los proyectos se cargan en segundo plano, lo que permite al usuario acceder a los proyectos que se cargan sin tener que esperar hasta que se cargan todos los proyectos.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: los proyectos se cargan cuando se accede a estos. Se tiene acceso a un proyecto cuando el usuario expande el nodo del proyecto en el Explorador de soluciones, cuando se abre un archivo que pertenecen al proyecto cuando se abre la solución porque está en la lista de documentos abiertos (guardada en el archivo de opciones de usuario de la solución), o cuando otro proyecto es decir que se está cargando tiene una dependencia en el proyecto. Este tipo de proyecto no se carga automáticamente antes de iniciar un proceso de compilación; el Administrador de carga de la solución es responsable de garantizar que todos los proyectos necesarios están cargados. Estos proyectos también se deben cargar antes de iniciar una Buscar/Reemplazar en archivos en toda la solución.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: los proyectos no son va a cargar, a menos que el usuario lo solicita explícitamente. Esto sucede cuando los proyectos se descargan explícitamente.  
  
## <a name="creating-a-solution-load-manager"></a>Creación de una carga de solución manager  
 Los desarrolladores pueden crear una carga de solución manager implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> y avisa de Visual Studio que el Administrador de carga de la solución está activo.  
  
#### <a name="activating-a-solution-load-manager"></a>Activación de un administrador de carga de la solución  
 Visual Studio permite a solo un administrador de carga de solución en un momento dado, por lo que deberá notificar a Visual Studio cuando desea activar la carga de la solución manager. Si un administrador de carga de solución segundo se activa más adelante, se desconectará el Administrador de carga de la solución.  
  
 Debe obtener el <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> de servicio y establezca el <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> propiedad:  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### <a name="implementing-ivssolutionloadmanager"></a>Implementar IVsSolutionLoadManager  
 El <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A> método se llama durante el proceso de abrir la solución. Para implementar este método, debe utilizar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport> servicio para establecer la prioridad de carga para el tipo de proyecto que se va a administrar. Por ejemplo, el código siguiente establece tipos de proyecto de C# para cargar en segundo plano:  
  
```csharp  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}");  
pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 El <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> método se llama cuando Visual Studio se está cerrando o cuando un paquete diferente ha asumido como el Administrador de carga de soluciones activas mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> con el <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> propiedad.  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Estrategias para distintos tipos de administrador de carga de la solución  
 Puede implementar administradores de carga de solución de maneras diferentes, dependiendo de los tipos de soluciones que están concebidos para administrar.  
  
 Si el Administrador de carga de la solución se ha diseñado para administrar soluciones cargar por lo general, se puede implementar como parte de un paquete VSPackage. El paquete debe establecerse para cargar automáticamente agregando el <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> en el VSPackage con un valor de <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>. A continuación, se puede activar el Administrador de carga de la solución en el <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método.  
  
> [!NOTE]
>  Para obtener más información acerca de los paquetes de carga automática, consulte [cargar VSPackages](../extensibility/loading-vspackages.md).  
  
 Dado que Visual Studio reconoce solo la última solución carga manager que se debe activar, administradores de la carga de la solución general siempre deberían detectar si hay un administrador de carga existente antes de activar por sí mismos. Si una llamada a GetProperty() en el servicio de la solución para <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> devuelve `null`, no hay ningún administrador de carga de la solución activa. Si no devuelve null, compruebe si el objeto es el mismo que el Administrador de carga de la solución.  
  
 Si el Administrador de carga de la solución se ha diseñado para administrar solo unos tipos de soluciones, el VSPackage puede suscribirse a eventos de carga de solución (mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>) y usar el controlador de eventos <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> para activar el Administrador de carga de la solución.  
  
 Si el Administrador de carga de la solución se ha diseñado para administrar solo soluciones específicas, se puede conservar la información de activación como parte del archivo de solución. Para ello, llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> para la sección de solución anterior.  
  
 Administradores de carga de solución específica que deberían desactivarse por sí mismos en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> controlador de eventos, en orden no entra en conflicto con otros administradores de carga de la solución.  
  
 Si necesita un administrador de carga de la solución solo para conservar las prioridades del proyecto global carga (por ejemplo, se establecen en una página de opciones), puede activar el Administrador de carga de la solución en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> controlador de eventos, la configuración en las propiedades de la solución, a continuación, se conservan desactivar el Administrador de carga de la solución.  
  
## <a name="handling-solution-load-events"></a>Control de eventos de carga de solución  
 Para suscribirse a eventos de carga de la solución, llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> cuando activa el Administrador de carga de la solución. Si implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, se puede responder a eventos relacionados con proyectos diferentes prioridades de carga.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Se desencadena antes de abre una solución. Puede usarlo para cambiar el proyecto cargar prioridad para los proyectos de la solución.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Esto se activa después de la solución está completamente cargada, pero antes de fondo proyecto cargar comienza de nuevo. Por ejemplo, un usuario podría haber accedido a un proyecto cuya prioridad de carga es LoadIfNeeded o el Administrador de carga de la solución puede haber cambiado una prioridad de carga del proyecto a BackgroundLoad, que empezarán a una carga en segundo plano de ese proyecto.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Si no hay un administrador de carga de la solución Esto se activa después de una solución está inicialmente totalmente cargada. También se desencadena después de carga en segundo plano o petición carga cada vez que la solución pasa a ser totalmente cargada. Al mismo tiempo, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> se reactiva.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Esto se activa antes de la carga de un proyecto (o proyectos). Para asegurarse de que otros procesos en segundo plano se completan antes de que los proyectos se carguen, establezca `pfShouldDelayLoadToNextIdle` a **true**.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Se activa cuando un lote de proyectos se va a cargarse. Si `fIsBackgroundIdleBatch` es true, los proyectos son que se carguen en segundo plano; si `fIsBackgroundIdleBatch` es false, los proyectos que van a ser cargado de forma sincrónica como resultado de una solicitud de usuario, por ejemplo, si el usuario expande un proyecto pendiente en el Explorador de soluciones. Puede hacerlo para realizar trabajo costoso que en caso contrario, tendría que hacer en <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Esto se activa después de que se ha cargado un lote de proyectos.  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>Detectar y administrar soluciones y carga del proyecto  
 Con el fin de detectar el estado de carga de los proyectos y soluciones, llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> con los valores siguientes:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` devuelve `true` si la solución y todos sus proyectos se cargan, de lo contrario `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` devuelve `true` si un lote de proyectos que se va a cargadas actualmente en segundo plano, de lo contrario `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` devuelve `true` si un lote de proyectos están actualmente está cargado de forma sincrónica como resultado de un comando de usuario u otra carga explícita, en caso contrario, `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` devuelve `true` si la solución actualmente se cierra, en caso contrario, `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` devuelve `true` si una solución actualmente se abre, en caso contrario, `false`.  
  
 También puede asegurarse de que se cargan los proyectos y soluciones (sin importar cuáles sean las prioridades de carga del proyecto) llamando a uno de los métodos siguientes:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: llamar a este método obliga a los proyectos de una solución para cargar antes de que el método devuelve.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: llamar a este método obliga a los proyectos de `guidProject` cargar antes de que el método devuelve.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: llamar a este método fuerza el proyecto en `guidProjectID` cargar antes de que el método devuelve.  
  
> [!NOTE]
>  . De forma predeterminada sólo los proyectos que tienen la demanda de carga y se cargan las prioridades de carga de segundo plano, pero si el <xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS> marca se pasa al método, se cargarán todos los proyectos excepto los que están marcados para cargar explícitamente.