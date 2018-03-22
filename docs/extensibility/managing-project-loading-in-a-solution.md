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
ms.openlocfilehash: 2dbbb8ddcf574f2e3db81ce63db257e21ff88839
ms.sourcegitcommit: a80e7ef2f0a0f6d906a44f4d696aeb208bc1ad70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2018
---
# <a name="managing-project-loading-in-a-solution"></a>Administrar la carga de proyecto en una solución
Soluciones de Visual Studio pueden contener un gran número de proyectos. El comportamiento predeterminado de Visual Studio es cargar todos los proyectos en una solución en el momento en que se abre la solución y no permite al usuario tener acceso a cualquiera de los proyectos hasta que todas ellas han terminado de cargarse. Cuando el proceso de carga de proyecto durará más de dos minutos, se muestra una barra de progreso que muestra el número de proyectos cargados y el número total de proyectos. El usuario puede descargar proyectos mientras trabaja en una solución con varios proyectos, pero este procedimiento tiene algunas desventajas: no se compilan los proyectos de descargados como parte de un comando de volver a generar solución, y las descripciones de IntelliSense de tipos y miembros de cerrado no se muestran los proyectos.  
  
 Los desarrolladores pueden reducir los tiempos de carga de solución y administrar el comportamiento de carga mediante la creación de una carga de la solución el administrador del proyecto. El Administrador de carga de la solución puede asegurarse de que los proyectos se cargan antes de iniciar una compilación de fondo, retrasar la carga de fondo hasta que finalicen otras tareas en segundo plano y realizar otras tareas de administración de la carga de proyecto.  
  
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
  
 El <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> método se llama cuando Visual Studio se está cerrando o cuando un paquete diferente ha asumido como el Administrador de carga de soluciones activas mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> con el <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> propiedad.  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Estrategias para distintos tipos de administrador de carga de la solución  
 Puede implementar administradores de carga de solución de maneras diferentes, dependiendo de los tipos de soluciones que están concebidos para administrar.  
  
 Si el Administrador de carga de la solución se ha diseñado para administrar soluciones cargar por lo general, se puede implementar como parte de un paquete VSPackage. El paquete debe establecerse para cargar automáticamente agregando el <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> en el VSPackage con un valor de <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>. A continuación, se puede activar el Administrador de carga de la solución en el <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método.  
  
> [!NOTE]
>  Para obtener más información acerca de los paquetes de carga automática, consulte [cargar VSPackages](../extensibility/loading-vspackages.md).  
  
 Dado que Visual Studio reconoce solo la última solución carga manager que se debe activar, administradores de la carga de la solución general siempre deberían detectar si hay un administrador de carga existente antes de activar por sí mismos. Si una llamada a GetProperty() en el servicio de la solución para <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> devuelve `null`, no hay ningún administrador de carga de la solución activa. Si no devuelve null, compruebe si el objeto es el mismo que el Administrador de carga de la solución.  
  
 Si el Administrador de carga de la solución se ha diseñado para administrar solo unos tipos de soluciones, el VSPackage puede suscribirse a eventos de carga de solución (mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>) y usar el controlador de eventos <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> para activar el Administrador de carga de la solución.  
  
 Si el Administrador de carga de la solución se ha diseñado para administrar solo soluciones específicas, la información de activación se puede conservar como parte del archivo de solución mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> para la sección de solución anterior.  
  
 Administradores de carga de solución específica que deberían desactivarse por sí mismos en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> controlador de eventos, en orden no entra en conflicto con otros administradores de carga de la solución.  
  
 Si necesita un administrador de carga de la solución solo para conservar propiedades de carga global del proyecto (por ejemplo, se establecen en una página de opciones), puede activar el Administrador de carga de la solución en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> controlador de eventos, la configuración en las propiedades de la solución, a continuación, se conservan desactivar el Administrador de carga de la solución.  
  
## <a name="handling-solution-load-events"></a>Control de eventos de carga de solución  
 Para suscribirse a eventos de carga de la solución, llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> cuando activa el Administrador de carga de la solución. Si implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, puede responder a eventos que se relacionan a cargar las propiedades de proyecto diferente.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Este evento se desencadena antes de abre una solución.
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Este evento se desencadena después de que la solución está completamente cargada pero antes de fondo proyecto cargar comienza de nuevo.
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Este evento se desencadena después de carga totalmente inicialmente una solución, si no hay un administrador de carga de la solución. También se desencadena después de carga en segundo plano o petición carga cada vez que la solución pasa a ser totalmente cargada. Al mismo tiempo, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> se reactiva.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Este evento se desencadena antes de la carga de un proyecto (o proyectos). Para asegurarse de que otros procesos en segundo plano se completan antes de que los proyectos se carguen, establezca `pfShouldDelayLoadToNextIdle` a **true**.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Este evento se desencadena cuando un lote de proyectos se va a cargarse. Si `fIsBackgroundIdleBatch` es true, los proyectos son que se carguen en segundo plano; si `fIsBackgroundIdleBatch` es false, los proyectos que van a ser cargado de forma sincrónica como resultado de una solicitud de usuario, por ejemplo, si el usuario expande un proyecto pendiente en el Explorador de soluciones. Puede controlar este evento para realizar trabajo costoso que en caso contrario, tendría que hacer en <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Este evento se desencadena después de que se ha cargado un lote de proyectos.  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>Detectar y administrar soluciones y carga del proyecto  
 Con el fin de detectar el estado de carga de los proyectos y soluciones, llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> con los valores siguientes:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` devuelve `true` si la solución y todos sus proyectos se cargan, de lo contrario `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` devuelve `true` si un lote de proyectos que se va a cargada en segundo plano, de lo contrario `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` devuelve `true` si un lote de proyectos es actualmente está cargado de forma sincrónica como resultado de un comando de usuario u otra carga explícita, de lo contrario `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` devuelve `true` si la solución actualmente se cierra, en caso contrario, `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` devuelve `true` si una solución actualmente se abre, en caso contrario, `false`.  
  
 También puede asegurarse de que los proyectos y soluciones se cargan llamando a uno de los métodos siguientes:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: llamar a este método obliga a los proyectos de una solución para cargar antes de que el método devuelve.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: llamar a este método obliga a los proyectos de `guidProject` cargar antes de que el método devuelve.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: llamar a este método fuerza el proyecto en `guidProjectID` cargar antes de que el método devuelve.  
