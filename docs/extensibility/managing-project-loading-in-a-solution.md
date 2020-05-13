---
title: Gestión de la carga de proyectos en una solución ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21cd5e7e557e795db49aea7a14e8e4cc7caa0422
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702733"
---
# <a name="manage-project-loading-in-a-solution"></a>Gestionar la carga de proyectos en una solución
Las soluciones de Visual Studio pueden contener un gran número de proyectos. El comportamiento predeterminado de Visual Studio es cargar todos los proyectos en una solución en el momento en que se abre la solución y no permitir que el usuario tenga acceso a ninguno de los proyectos hasta que todos ellos hayan terminado de cargarse. Cuando el proceso de carga del proyecto durará más de dos minutos, se muestra una barra de progreso que muestra el número de proyectos cargados y el número total de proyectos. El usuario puede descargar proyectos mientras trabaja en una solución con varios proyectos, pero este procedimiento tiene algunas desventajas: los proyectos descargados no se compilan como parte de un comando Reconstruir solución y no se muestran descripciones de IntelliSense de tipos y miembros de proyectos cerrados.

 Los desarrolladores pueden reducir los tiempos de carga de la solución y administrar el comportamiento de carga de proyectos mediante la creación de un administrador de carga de soluciones. El administrador de carga de soluciones puede asegurarse de que los proyectos se cargan antes de iniciar una compilación en segundo plano, retrasar la carga en segundo plano hasta que se completen otras tareas en segundo plano y realizar otras tareas de administración de carga de proyectos.

## <a name="create-a-solution-load-manager"></a>Crear un gestor de carga de soluciones
 Los desarrolladores pueden crear <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> un administrador de carga de soluciones implementando y aconsejando a Visual Studio que el administrador de carga de la solución está activo.

### <a name="activate-a-solution-load-manager"></a>Activar un gestor de carga de soluciones
 Visual Studio solo permite un administrador de carga de solución en un momento dado, por lo que debe informar a Visual Studio cuando desee activar el administrador de carga de la solución. Si un administrador de carga de segunda solución se activa más adelante, el administrador de carga de la solución se desconectará.

 Debe obtener <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> el servicio y establecer el [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) propiedad:

```csharp
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;
object objLoadMgr = this;   //the class that implements IVsSolutionManager
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);
```

 Se <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> llama al método cuando Visual Studio se está cerrando o cuando un paquete <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> diferente se ha tomado el control como el administrador de carga de la solución activa mediante una llamada con el [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) propiedad.

#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Estrategias para diferentes tipos de gestor de carga de soluciones
 Puede implementar administradores de carga de soluciones de diferentes maneras, dependiendo de los tipos de soluciones que están destinados a administrar.

 Si el administrador de carga de la solución está diseñado para administrar la carga de la solución en general, se puede implementar como parte de un VSPackage. El paquete debe establecerse en <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> autoload agregando el <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>VSPackage con un valor de . El administrador de carga de <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> la solución se puede activar en el método.

> [!NOTE]
> Para obtener más información acerca de la carga automática de paquetes, vea [Cargar VSPackages](../extensibility/loading-vspackages.md).

 Dado que Visual Studio reconoce solo el último administrador de carga de solución que se va a activar, los administradores de carga de soluciones generales siempre deben detectar si hay un administrador de carga existente antes de activarse a sí mismos. Si `GetProperty()` llama al servicio de solución para [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) `null`devuelve , no hay ningún administrador de carga de solución activo. Si no devuelve null, compruebe si el objeto es el mismo que el administrador de carga de la solución.

 Si el administrador de carga de la solución está diseñado para administrar solo unos <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>pocos tipos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> solución, el VSPackage puede suscribirse a eventos de carga de la solución (mediante una llamada ) y usar el controlador de eventos para activar el administrador de carga de la solución.

 Si el administrador de carga de soluciones está diseñado para administrar solo soluciones específicas, la información de activación se puede conservar como parte del archivo de solución llamando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> la sección previa a la solución.

 Los administradores de carga de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> soluciones específicos deben desactivarse en el controlador de eventos, para no entrar en conflicto con otros administradores de carga de soluciones.

 Si necesita un administrador de carga de soluciones solo para conservar las propiedades de carga global del <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> proyecto (por ejemplo, las propiedades establecidas en una página Opciones), puede activar el administrador de carga de la solución en el controlador de eventos, conservar la configuración en las propiedades de la solución y, a continuación, desactivar el administrador de carga de la solución.

## <a name="handle-solution-load-events"></a>Controlar eventos de carga de soluciones
 Para suscribirse a eventos <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> de carga de soluciones, llame cuando active el administrador de carga de soluciones. Si implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, puede responder a eventos relacionados con diferentes propiedades de carga de proyectos.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: este evento se desencadena antes de que se abra una solución.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: este evento se desencadena después de que la solución se haya cargado por completo, pero antes de que la carga del proyecto en segundo plano comience de nuevo.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: este evento se desencadena después de que una solución se haya cargado inicialmente por completo, independientemente de si hay o no un administrador de carga de la solución. También se desencadena después de la carga en segundo plano o la carga de demanda cada vez que la solución se carga por completo. Al mismo tiempo, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> se reactiva.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: este evento se desencadena antes de la carga de un proyecto (o proyectos). Para asegurarse de que se completan otros `pfShouldDelayLoadToNextIdle` procesos en segundo plano antes de cargar los proyectos, establezca **true**.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: este evento se desencadena cuando un lote de proyectos está a punto de cargarse. Si `fIsBackgroundIdleBatch` es true, los proyectos se cargarán en segundo plano; si `fIsBackgroundIdleBatch` es false, los proyectos se cargarán sincrónicamente como resultado de una solicitud de usuario, por ejemplo, si el usuario expande un proyecto pendiente en el Explorador de soluciones. Puede controlar este evento para realizar un trabajo costoso <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>que, de lo contrario, tendría que realizarse en .

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: este evento se desencadena después de cargar un lote de proyectos.

## <a name="detect-and-manage-solution-and-project-loading"></a>Detectar y gestionar la carga de soluciones y proyectos
 Para detectar el estado de carga de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> proyectos y soluciones, llame con los siguientes valores:

- [__VSPROPID4. VSPROPID_IsSolutionFullyLoaded](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsSolutionFullyLoaded>) `var` : `true` devuelve si se carga la `false`solución y todos sus proyectos, de lo contrario .

- [__VSPROPID4. VSPROPID_IsInBackgroundIdleLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInBackgroundIdleLoadProjectBatch>) `var` : `true` devuelve si se está cargando un `false`lote de proyectos en segundo plano, de lo contrario .

- [__VSPROPID4. VSPROPID_IsInSyncDemandLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInSyncDemandLoadProjectBatch>) `var` : `true` devuelve si un lote de proyectos se está cargando sincrónicamente `false`como resultado de un comando de usuario u otra carga explícita, de lo contrario .

- [__VSPROPID2. VSPROPID_IsSolutionClosing](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2.VSPROPID_IsSolutionClosing>) `var` : `true` devuelve si la solución `false`se está cerrando actualmente, de lo contrario .

- [__VSPROPID. VSPROPID_IsSolutionOpening](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID.VSPROPID_IsSolutionOpening>) `var` : `true` devuelve si se está `false`abrendo una solución, de lo contrario .

También puede asegurarse de que los proyectos y soluciones se cargan llamando a uno de los métodos siguientes:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: llamar a este método fuerza los proyectos de una solución para cargar antes de que se devuelva el método.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: llamar a este `guidProject` método obliga a los proyectos a cargarse antes de que se devuelva el método.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: llamar a este `guidProjectID` método obliga al proyecto a cargarse antes de que se devuelva el método.
