---
title: "Interfaz de usuario personalizada (VSPackage de Control de código fuente) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3d3c223b45d0228781779a73f057ef3518374344
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="custom-user-interface-source-control-vspackage"></a>Interfaz de usuario personalizada (VSPackage de Control de código fuente)
Un VSPackage declara sus elementos de menú y sus estados predeterminados a través del archivo de la tabla de comandos de Visual Studio (.vsct). El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE) muestra los elementos de menú de sus estados predeterminados hasta que se cargue el VSPackage. Posteriormente, el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método se llama para habilitar o deshabilitar elementos de menú.  
  
 Un VSPackage puede establecer una clave del registro para que el VSPackage se puede cargar automáticamente según un contexto de interfaz de usuario de comandos, aunque normalmente controlar un origen de VSPackage debe cargar a petición en lugar de simplemente cambia a un determinado contexto de interfaz de usuario. Para obtener más información acerca de la clave de registro AutoLoadPackages, consulte [administrar VSPackages](../../extensibility/managing-vspackages.md).  
  
## <a name="vspackage-ui"></a>Interfaz de usuario de VSPackage  
 Un paquete de control de código fuente se implementa como un paquete VSPackage y no utiliza ninguna interfaz de usuario de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Cada control de código fuente VSPackage debe especificar sus propios elementos de interfaz de usuario como elementos de menú, grupos de menús, ventanas de herramientas, barras de herramientas y cualquier interfaz de usuario necesario para establecer las opciones específicas para el control de código fuente VSPackage. Estos elementos de interfaz de usuario pueden habilitarse de forma estática o dinámica. Elementos de interfaz de usuario estáticos se definen en un archivo .vsct y se muestran si el VSPackage se carga o no. Elementos de interfaz de usuario dinámicos pueden verse según un contexto de interfaz de usuario de ese comando concreto, como <xref:EnvDTE.Constants.vsContextNoSolution>, o como resultado de una llamada a la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método. La visibilidad de los elementos dinámicos de interfaz de usuario es compatible con la estrategia de carga retrasada de VSPackages.  
  
## <a name="ui-constraints-on-source-control-vspackages"></a>Restricciones de interfaz de usuario en VSPackages de Control de código fuente  
 Dado que el IDE no se puede quitar el control de código fuente VSPackage después de cargarlo, el VSPackage debe ser puede entrar en un estado inactivo. Cuando un paquete VSPackage recibe notificación de que ya no está activo, el VSPackage deshabilita su interfaz de usuario y omite cualquier interacción IDE externa. Implementación de VSPackage de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método debe ocultar comandos cuando el VSPackage no está activo.  
  
 Cada control de código fuente VSPackage debe implementar la `IVsSccProvider` interfaz. Dos métodos en la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>, debe ser implementada por el VSPackage.  
  
 El control de código fuente VSPackage puede ha suscrito a varios eventos IDE, que se implementan mediante la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>, y así sucesivamente. Además, el VSPackage puede haber implementado interfaces de devolución de llamada de registro habilitados, como el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>. Estos todos se deben omitir cuando esté inactivo.  
  
 La siguiente lista muestra las interfaces que se ve afectadas por el estado activo de un control de código fuente VSPackage:  
  
-   Realizar el seguimiento de eventos de documentos del proyecto.  
  
-   Eventos de la solución.  
  
-   Interfaces de persistencia de solución. Cuando esté inactivo, no deben escribir paquetes a los archivos .sln y. suo.  
  
-   Extensores de propiedad.  
  
 Requerido <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, y también las interfaces opcionales asociadas con el control de código fuente, no se llama cuando el control de código fuente VSPackage está inactivo.  
  
 Cuando el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] empieza a IDE, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] establece el contexto de la interfaz de usuario de comandos para el identificador del control de origen de valor predeterminado actual Id. de VSPackage. Esto hace que la interfaz de usuario estático del control de origen activo VSPackage que aparezca en el IDE sin que se está cargando realmente el VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]hace una pausa para que el VSPackage registrar con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> antes de efectuar cualquier llamada al VSPackage.  
  
 La tabla siguiente describe los detalles específicos acerca de cómo los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE oculta diferentes elementos de interfaz de usuario.  
  
|Elemento de interfaz de usuario|Descripción|  
|-------------|-----------------|  
|Menús y barras de herramientas|El paquete de control de origen debe establecer los Estados de visibilidad iniciales de barra de menús y en el identificador del paquete de control de código fuente en el [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) sección del archivo vsct. Esto permite la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE para establecer el estado de los elementos de menú correctamente sin tener que cargar el VSPackage y llamar a una implementación de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método.|  
|Ventanas de herramientas|El control de código fuente VSPackage oculta las ventanas de herramienta posee cuando queda inactiva.|  
|Páginas de opciones de control de código fuente específica de VSPackage|La clave del registro HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts permite un VSPackage establecer los contextos en los que requiere que se muestren sus páginas de opciones. Una entrada del registro bajo esta clave que se creó utilizando el servicio Id. (SID) del servicio de control de código fuente y asignarle un valor DWORD de 1. Cada vez que un evento de interfaz de usuario produce en un contexto de VSPackage se registra con el control de código fuente, se llamará el VSPackage si está activa.|  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>   
 <xref:EnvDTE.Constants.vsContextNoSolution>   
 [Administración de VSPackages](../../extensibility/managing-vspackages.md)