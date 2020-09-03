---
title: Administrar la carga de proyectos en una solución | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702733"
---
# <a name="manage-project-loading-in-a-solution"></a>Administrar la carga de proyectos en una solución
Las soluciones de Visual Studio pueden contener un gran número de proyectos. El comportamiento predeterminado de Visual Studio es cargar todos los proyectos de una solución en el momento en que se abre la solución y no permitir que el usuario tenga acceso a ninguno de los proyectos hasta que todos ellos hayan terminado de cargarse. Cuando el proceso de carga del proyecto dure más de dos minutos, se muestra una barra de progreso que muestra el número de proyectos cargados y el número total de proyectos. El usuario puede descargar proyectos mientras trabaja en una solución con varios proyectos, pero este procedimiento tiene algunas desventajas: los proyectos descargados no se compilan como parte de un comando recompilar solución y no se muestran las descripciones de IntelliSense de tipos y miembros de proyectos cerrados.

 Los desarrolladores pueden reducir los tiempos de carga de la solución y administrar el comportamiento de carga del proyecto mediante la creación de un administrador de carga de soluciones. El administrador de carga de soluciones puede asegurarse de que los proyectos se carguen antes de iniciar una compilación en segundo plano, retrasar la carga en segundo plano hasta que se completen otras tareas en segundo plano y realizar otras tareas de administración de carga del proyecto.

## <a name="create-a-solution-load-manager"></a>Crear un administrador de carga de soluciones
 Los desarrolladores pueden crear un administrador de carga de soluciones implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> e asesorando a Visual Studio de que el administrador de carga de soluciones está activo.

### <a name="activate-a-solution-load-manager"></a>Activar un administrador de carga de soluciones
 Visual Studio solo permite un administrador de carga de soluciones en un momento dado, por lo que debe notificar a Visual Studio Cuándo desea activar el administrador de carga de la solución. Si un segundo administrador de carga de soluciones se activa posteriormente en, el administrador de carga de soluciones se desconectará.

 Debe obtener el <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> servicio y establecer el [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) propiedad:

```csharp
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;
object objLoadMgr = this;   //the class that implements IVsSolutionManager
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);
```

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A>Se llama al método cuando se está cerrando Visual Studio o cuando un paquete diferente se ha tomado como el administrador de carga de soluciones activo mediante una llamada <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> a con el [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) propiedad.

#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Estrategias para diferentes tipos de administrador de carga de soluciones
 Puede implementar administradores de carga de soluciones de maneras diferentes, en función de los tipos de soluciones que están diseñadas para administrar.

 Si el administrador de carga de soluciones está diseñado para administrar la carga de la solución en general, se puede implementar como parte de un VSPackage. El paquete se debe establecer en autoload agregando <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> en el VSPackage con un valor de <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid> . Después, el administrador de carga de soluciones se puede activar en el <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método.

> [!NOTE]
> Para obtener más información acerca de la carga de paquetes, vea [cargar VSPackages](../extensibility/loading-vspackages.md).

 Dado que Visual Studio solo reconoce el último administrador de carga de soluciones que se va a activar, los administradores de carga de soluciones generales deben detectar siempre si hay un administrador de carga existente antes de activarse. Si se llama a `GetProperty()` en el servicio de solución para [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) devuelve `null` , no hay ningún administrador de carga de soluciones activo. Si no devuelve null, compruebe si el objeto es el mismo que el administrador de carga de soluciones.

 Si el administrador de carga de soluciones está diseñado para administrar solo unos pocos tipos de soluciones, el VSPackage puede suscribirse a eventos de carga de solución (llamando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> ) y usar el controlador de eventos para <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> para activar el administrador de carga de soluciones.

 Si el administrador de carga de soluciones está pensado para administrar solo soluciones específicas, la información de activación se puede guardar como parte del archivo de solución llamando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> para la sección de la solución anterior.

 Los administradores de carga de solución específicos deben desactivarse en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> controlador de eventos, por lo que no entrarán en conflicto con otros administradores de carga de soluciones.

 Si necesita un administrador de carga de soluciones solo para conservar las propiedades globales de carga del proyecto (por ejemplo, las propiedades establecidas en una página de opciones), puede activar el administrador de carga de soluciones en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> controlador de eventos, conservar la configuración en las propiedades de la solución y, a continuación, desactivar el administrador de carga de soluciones.

## <a name="handle-solution-load-events"></a>Controlar los eventos de carga de la solución
 Para suscribirse a los eventos de carga de la solución, llame <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> al activar el administrador de carga de la solución. Si implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents> , puede responder a los eventos relacionados con las distintas propiedades de carga del proyecto.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Este evento se desencadena antes de que se abra una solución.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Este evento se desencadena después de que la solución se haya cargado por completo, pero antes de que se vuelva a cargar el proyecto en segundo plano.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Este evento se desencadena después de que una solución se haya cargado por completo, independientemente de si hay un administrador de carga de soluciones. También se desencadena después de la carga en segundo plano o la carga de demanda cada vez que la solución se carga por completo. Al mismo tiempo, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> se reactiva.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Este evento se desencadena antes de cargar un proyecto (o proyectos). Para asegurarse de que se completan otros procesos en segundo plano antes de que se carguen los proyectos, establezca `pfShouldDelayLoadToNextIdle` en **true**.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Este evento se desencadena cuando un lote de proyectos está a punto de cargarse. Si `fIsBackgroundIdleBatch` es true, los proyectos se cargarán en segundo plano; si `fIsBackgroundIdleBatch` es false, los proyectos se cargarán de forma sincrónica como resultado de una solicitud de usuario, por ejemplo, si el usuario expande un proyecto pendiente en explorador de soluciones. Puede controlar este evento para realizar un trabajo costoso que, de lo contrario, tendría que realizarse en <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> .

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Este evento se desencadena después de que se haya cargado un lote de proyectos.

## <a name="detect-and-manage-solution-and-project-loading"></a>Detección y administración de la carga de soluciones y proyectos
 Para detectar el estado de carga de los proyectos y las soluciones, llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> con los siguientes valores:

- [__VSPROPID4. VSPROPID_IsSolutionFullyLoaded](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsSolutionFullyLoaded>): `var` devuelve `true` si se cargan la solución y todos sus proyectos; de lo contrario, devuelve `false` .

- [__VSPROPID4. VSPROPID_IsInBackgroundIdleLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInBackgroundIdleLoadProjectBatch>): `var` devuelve `true` si un lote de proyectos se está cargando actualmente en segundo plano; de lo contrario, devuelve `false` .

- [__VSPROPID4. VSPROPID_IsInSyncDemandLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInSyncDemandLoadProjectBatch>): `var` devuelve `true` si un lote de proyectos se está cargando sincrónicamente como resultado de un comando de usuario u otra carga explícita; de lo contrario, `false` .

- [__VSPROPID2. VSPROPID_IsSolutionClosing](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2.VSPROPID_IsSolutionClosing>): `var` devuelve `true` si la solución se está cerrando actualmente; de lo contrario, devuelve `false` .

- [__VSPROPID. VSPROPID_IsSolutionOpening](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID.VSPROPID_IsSolutionOpening>): `var` devuelve `true` si una solución se está abriendo actualmente, de lo contrario, `false` .

También puede asegurarse de que los proyectos y las soluciones se cargan llamando a uno de los métodos siguientes:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: la llamada a este método obliga a que los proyectos de una solución se carguen antes de que el método devuelva.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: la llamada a este método obliga a que los proyectos de `guidProject` se carguen antes de que el método devuelva.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: si se llama a este método, se fuerza la carga del proyecto `guidProjectID` antes de que el método devuelva.
