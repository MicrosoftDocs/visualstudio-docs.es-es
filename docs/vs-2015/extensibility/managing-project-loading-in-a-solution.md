---
title: Administrar la carga de proyectos en una solución | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a6598e2f1a178845b3ad2017716576439185379e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842454"
---
# <a name="managing-project-loading-in-a-solution"></a>Administración de la carga de proyectos en una solución
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las soluciones de Visual Studio pueden contener un gran número de proyectos. El comportamiento predeterminado de Visual Studio es cargar todos los proyectos de una solución en el momento en que se abre la solución y no permitir que el usuario tenga acceso a ninguno de los proyectos hasta que todos ellos hayan terminado de cargarse. Cuando el proceso de carga del proyecto dure más de dos minutos, se muestra una barra de progreso que muestra el número de proyectos cargados y el número total de proyectos. El usuario puede descargar proyectos mientras trabaja en una solución con varios proyectos, pero este procedimiento tiene algunas desventajas: los proyectos descargados no se compilan como parte de un comando recompilar solución y no se muestran las descripciones de IntelliSense de tipos y miembros de proyectos cerrados.  
  
 Los desarrolladores pueden reducir los tiempos de carga de la solución y administrar el comportamiento de carga del proyecto mediante la creación de un administrador de carga de soluciones. El administrador de carga de soluciones puede establecer diferentes prioridades de carga de proyectos para proyectos o tipos de proyecto específicos, asegurarse de que los proyectos se cargan antes de iniciar una compilación en segundo plano, retrasar la carga en segundo plano hasta que se completen otras tareas en segundo plano y realizar otras tareas de administración de carga del proyecto.  
  
## <a name="project-loading-priorities"></a>Prioridades de carga del proyecto  
 Visual Studio define cuatro prioridades de carga de proyectos diferentes:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority> (valor predeterminado): cuando se abre una solución, los proyectos se cargan de forma asincrónica. Si esta prioridad se establece en un proyecto descargado una vez que la solución ya está abierta, el proyecto se cargará en el siguiente punto inactivo.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: cuando se abre una solución, los proyectos se cargan en segundo plano, lo que permite al usuario acceder a los proyectos a medida que se cargan sin tener que esperar hasta que se carguen todos los proyectos.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: los proyectos se cargan cuando se tiene acceso a ellos. Se tiene acceso a un proyecto cuando el usuario expande el nodo del proyecto en el Explorador de soluciones, cuando se abre un archivo que pertenece al proyecto cuando se abre la solución porque está en la lista de documentos abiertos (persistente en el archivo de opciones de usuario de la solución) o cuando otro proyecto que se está cargando tiene una dependencia en el proyecto. Este tipo de proyecto no se carga automáticamente antes de iniciar un proceso de compilación; el administrador de carga de soluciones es responsable de garantizar que se carguen todos los proyectos necesarios. Estos proyectos también se deben cargar antes de iniciar una búsqueda y reemplazo en los archivos de toda la solución.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: los proyectos no se cargarán a menos que el usuario lo solicite explícitamente. Este es el caso cuando los proyectos se descargan explícitamente.  
  
## <a name="creating-a-solution-load-manager"></a>Crear un administrador de carga de soluciones  
 Los desarrolladores pueden crear un administrador de carga de soluciones implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> e asesorando a Visual Studio de que el administrador de carga de soluciones está activo.  
  
#### <a name="activating-a-solution-load-manager"></a>Activar un administrador de carga de soluciones  
 Visual Studio solo permite un administrador de carga de soluciones en un momento dado, por lo que debe notificar a Visual Studio Cuándo desea activar el administrador de carga de la solución. Si un segundo administrador de carga de soluciones se activa posteriormente en, el administrador de carga de soluciones se desconectará.  
  
 Debe obtener el <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> servicio y establecer la <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> propiedad:  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### <a name="implementing-ivssolutionloadmanager"></a>Implementación de IVsSolutionLoadManager  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A>Se llama al método durante el proceso de apertura de la solución. Para implementar este método, utilice el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport> servicio para establecer la prioridad de carga para el tipo de proyecto que desea administrar. Por ejemplo, el código siguiente establece los tipos de proyecto de C# para cargarlos en segundo plano:  
  
```csharp  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}");  
pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A>Se llama al método cuando se está cerrando Visual Studio o cuando un paquete diferente se ha tomado como el administrador de carga de soluciones activo mediante una llamada <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> a con la <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> propiedad.  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Estrategias para diferentes tipos de administrador de carga de soluciones  
 Puede implementar administradores de carga de soluciones de maneras diferentes, en función de los tipos de soluciones que están diseñadas para administrar.  
  
 Si el administrador de carga de soluciones está diseñado para administrar la carga de la solución en general, se puede implementar como parte de un VSPackage. El paquete se debe establecer en autoload agregando <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> en el VSPackage con un valor de <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid> . Después, el administrador de carga de soluciones se puede activar en el <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método.  
  
> [!NOTE]
> Para obtener más información acerca de la carga de paquetes, vea [cargar VSPackages](../extensibility/loading-vspackages.md).  
  
 Dado que Visual Studio solo reconoce el último administrador de carga de soluciones que se va a activar, los administradores de carga de soluciones generales deben detectar siempre si hay un administrador de carga existente antes de activarse. Si la llamada a GetProperty () en el servicio de solución para <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> devuelve, no hay `null` ningún administrador de carga de soluciones activo. Si no devuelve null, compruebe si el objeto es el mismo que el administrador de carga de soluciones.  
  
 Si el administrador de carga de soluciones está diseñado para administrar solo unos pocos tipos de soluciones, el VSPackage puede suscribirse a eventos de carga de solución (llamando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> ) y usar el controlador de eventos para <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> para activar el administrador de carga de soluciones.  
  
 Si el administrador de carga de soluciones está pensado para administrar solo soluciones específicas, la información de activación se puede guardar como parte del archivo de solución. Para ello, llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> para la sección anterior a la solución.  
  
 Los administradores de carga de solución específicos deben desactivarse en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> controlador de eventos, por lo que no entrarán en conflicto con otros administradores de carga de soluciones.  
  
 Si necesita un administrador de carga de soluciones solo para conservar las prioridades globales de carga del proyecto (por ejemplo, las propiedades establecidas en una página de opciones), puede activar el administrador de carga de soluciones en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents2.OnAfterOpenProject%2A> controlador de eventos, conservar la configuración en las propiedades de la solución y, a continuación, desactivar el administrador de carga de soluciones.  
  
## <a name="handling-solution-load-events"></a>Controlar los eventos de carga de la solución  
 Para suscribirse a los eventos de carga de la solución, llame <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> al activar el administrador de carga de la solución. Si implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents> , puede responder a eventos que se relacionan con prioridades de carga de proyectos diferentes.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Esto se desencadena antes de que se abra una solución. Puede usarlo para cambiar la prioridad de carga del proyecto para los proyectos de la solución.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Esto se desencadena después de que la solución se haya cargado por completo, pero antes de que se vuelva a cargar el proyecto en segundo plano. Por ejemplo, es posible que un usuario haya tenido acceso a un proyecto cuya prioridad de carga sea LoadIfNeeded, o que el administrador de carga de soluciones haya cambiado una prioridad de carga del proyecto a BackgroundLoad, lo que iniciaría una carga en segundo plano de ese proyecto.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Esto se desencadena cuando una solución se carga por completo inicialmente, independientemente de si hay un administrador de carga de soluciones. También se desencadena después de la carga en segundo plano o la carga de demanda cada vez que la solución se carga por completo. Al mismo tiempo, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> se reactiva.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Esto se desencadena antes de cargar un proyecto (o proyectos). Para asegurarse de que se completan otros procesos en segundo plano antes de que se carguen los proyectos, establezca `pfShouldDelayLoadToNextIdle` en **true**.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Esto se desencadena cuando un lote de proyectos está a punto de cargarse. Si `fIsBackgroundIdleBatch` es true, los proyectos se cargarán en segundo plano; si `fIsBackgroundIdleBatch` es false, los proyectos se cargarán de forma sincrónica como resultado de una solicitud de usuario, por ejemplo, si el usuario expande un proyecto pendiente en explorador de soluciones. Puede implementar esto para realizar trabajo caro que, de lo contrario, tendría que realizarse en <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Esto se desencadena después de que se haya cargado un lote de proyectos.  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>Detección y administración de la carga de soluciones y proyectos  
 Para detectar el estado de carga de los proyectos y las soluciones, llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> con los siguientes valores:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` devuelve `true` si la solución y todos sus proyectos se cargan, de lo contrario, es `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` devuelve `true` si un lote de proyectos se está cargando actualmente en segundo plano; de lo contrario, devuelve `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` devuelve `true` si un lote de proyectos se está cargando sincrónicamente como resultado de un comando de usuario u otra carga explícita, de lo contrario, `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` devuelve `true` si la solución se está cerrando actualmente, de lo contrario, `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` devuelve `true` si una solución se está abriendo actualmente, de lo contrario, `false` .  
  
  También puede asegurarse de que los proyectos y las soluciones se cargan (independientemente de las prioridades de carga del proyecto) mediante una llamada a uno de los métodos siguientes:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: la llamada a este método obliga a que los proyectos de una solución se carguen antes de que el método devuelva.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: la llamada a este método obliga a que los proyectos de `guidProject` se carguen antes de que el método devuelva.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: si se llama a este método, se fuerza la carga del proyecto `guidProjectID` antes de que el método devuelva.  
  
> [!NOTE]
> . De forma predeterminada, solo se cargan los proyectos que tienen las prioridades de carga de la demanda y de carga en segundo plano, pero si la <xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS> marca se pasa al método, se cargarán todos los proyectos excepto los que estén marcados para cargarse explícitamente.
