---
title: Administrar la carga de proyectos en una solución | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1f861f765305dc0ea4bdfd83326a5a4888239033
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53870156"
---
# <a name="manage-project-loading-in-a-solution"></a>Administrar la carga del proyecto en una solución
Soluciones de Visual Studio pueden contener un gran número de proyectos. El comportamiento de Visual Studio predeterminado es cargar todos los proyectos de una solución en el momento en que se abra la solución y no permite al usuario tener acceso a cualquiera de los proyectos hasta que todos ellos han terminado de cargarse. Cuando el proceso de carga de proyecto durará más de dos minutos, se muestra una barra de progreso que muestra el número de proyectos cargados y el número total de los proyectos. El usuario puede descargar proyectos mientras trabaja en una solución con varios proyectos, pero este procedimiento tiene algunas desventajas: no se compilan los proyectos descargados como parte de un comando recompilar solución y las descripciones de IntelliSense de tipos y miembros de cerrado no se muestran los proyectos.  
  
 Los desarrolladores pueden reducir los tiempos de carga de solución y administrar el comportamiento de carga mediante la creación de una carga de solución administrador del proyecto. El Administrador de carga de solución puede asegurarse de que los proyectos se cargan antes de iniciar una compilación en segundo plano, retraso al cargar en segundo plano hasta que se completen otras tareas en segundo plano y realizar otras tareas de administración de carga de proyecto.  
  
## <a name="create-a-solution-load-manager"></a>Crear una carga de solución de administrador  
 Los desarrolladores pueden crear una carga de solución manager implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> y Visual Studio que avisa de que el Administrador de carga de solución está activo.  
  
### <a name="activate-a-solution-load-manager"></a>Activar un administrador de carga de solución  
 Visual Studio permite a solo un administrador de carga de solución en un momento dado, por lo que debe dar a conocer a Visual Studio cuando desea activar la carga de solución manager. Si un segundo administrador de carga de solución está activado más adelante, se desconectará el Administrador de carga de solución.  
  
 Debe obtener el <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> de servicio y establezca el <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> propiedad:  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
 El <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> llama al método cuando se cierra Visual Studio o cuando un paquete diferente ha asumido el Administrador de carga de soluciones activas mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> con el <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> propiedad.  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Estrategias para distintos tipos de administrador de carga de solución  
 Puede implementar administradores de la carga de solución de maneras diferentes, dependiendo de los tipos de soluciones que están diseñadas para administrar.  
  
 Si el Administrador de carga de solución se ha diseñado para administrar la carga en general de la solución, se puede implementar como parte de un paquete VSPackage. El paquete se debe establecer en autoload agregando el <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> en el VSPackage con un valor de <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>. A continuación, se puede activar el Administrador de carga de solución en el <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método.  
  
> [!NOTE]
>  Para obtener más información acerca de los paquetes de carga automática, consulte [cargar VSPackages](../extensibility/loading-vspackages.md).  
  
 Dado que Visual Studio reconoce solo la última solución Administrador de carga para activarse, administradores de la carga de solución general siempre deben detectar si hay un administrador de carga existente antes de activar a sí mismos. Si una llamada a `GetProperty()` en el servicio de la solución para <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> devuelve `null`, no hay ningún administrador de carga de solución activa. Si no se devuelve null, compruebe si el objeto es igual que el Administrador de carga de solución.  
  
 Si el Administrador de carga de solución se ha diseñado para administrar solo unos pocos tipos de soluciones, el VSPackage puede suscribirse a eventos de carga de solución (mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>) y usar el controlador de eventos <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> para activar el Administrador de carga de solución.  
  
 Si el Administrador de carga de solución se ha diseñado para administrar solo soluciones específicas, la información de activación se puede conservar como parte del archivo de solución mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> para la sección previa de la solución.  
  
 Administradores de la carga de solución específica que se deberían desactivar a sí mismos en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> controlador de eventos, para que no entran en conflicto con otros administradores de la carga de solución.  
  
 Si necesita un administrador de carga de solución solo para conservar las propiedades de carga global de proyectos (por ejemplo, propiedades establecidas en una página de opciones), puede activar el Administrador de carga de solución en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> controlador de eventos, conservar la configuración, a continuación, en las propiedades de la solución, desactivar el Administrador de carga de solución.  
  
## <a name="handle-solution-load-events"></a>Controlar eventos de carga de solución  
 Para suscribirse a eventos de carga de solución, llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> al activar el Administrador de carga de solución. Si implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, puede responder a eventos relacionados con cargar las propiedades de proyecto diferente.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Este evento se desencadena antes de que se abre una solución.
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Este evento se desencadena después de la solución se haya cargado, pero antes en segundo plano carga del proyecto comienza de nuevo.
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Este evento se desencadena después de carga inicialmente completamente una solución, si hay un administrador de carga de solución. También se desencadena después de carga en segundo plano o la demanda de carga siempre que se carguen por completo la solución. Al mismo tiempo, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> se vuelve a activar.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Este evento se desencadena antes de la carga de un proyecto (o proyectos). Para asegurarse de que otros procesos en segundo plano se completan antes de que se cargan los proyectos, establezca `pfShouldDelayLoadToNextIdle` a **true**.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Este evento se desencadena cuando un lote de proyectos está a punto de cargarse. Si `fIsBackgroundIdleBatch` es true, los proyectos son deben cargarse en segundo plano; si `fIsBackgroundIdleBatch` es false, los proyectos que van a cargarse sincrónicamente como resultado de una solicitud de usuario, por ejemplo si el usuario expande un proyecto pendiente en el Explorador de soluciones. Puede controlar este evento para realizar trabajo costoso que de lo contrario tendría que realizarse en <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Este evento se desencadena después de que se ha cargado un lote de proyectos.  
  
## <a name="detect-and-manage-solution-and-project-loading"></a>Detectar y administrar soluciones y la carga de proyectos  
 Para detectar el estado de carga de proyectos y soluciones, llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> con los valores siguientes:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` devuelve `true` si la solución y todos sus proyectos se cargan, de lo contrario `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` devuelve `true` si un lote de proyectos está cargado en segundo plano, de lo contrario `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` devuelve `true` si un lote de proyectos se está cargando actualmente sincrónicamente como resultado de un comando de usuario o de otros de la carga explícita, de lo contrario `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` devuelve `true` si la solución está actualmente está cerrada, de lo contrario `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` devuelve `true` si una solución está abierta actualmente, en caso contrario `false`.  
  
  También puede asegurarse de que los proyectos y soluciones se cargan llamando a uno de los métodos siguientes:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: llamar a este método obliga a los proyectos de una solución para cargar antes de que el método devuelve.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: llamar a este método obliga a los proyectos de `guidProject` cargar antes de que el método devuelve.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: llamar a este método fuerza el proyecto en `guidProjectID` cargar antes de que el método devuelve.  
