---
title: Interfaz de usuario personalizada (VSPackage de Control de código fuente) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bc8158325d975aec4bd522fddad2375001d2f72e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919356"
---
# <a name="custom-user-interface-source-control-vspackage"></a>Interfaz de usuario personalizada (VSPackage de control de código fuente)
Un VSPackage declara sus elementos de menú y sus estados predeterminados a través de la tabla de comandos de Visual Studio (*.vsct*) archivo. El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE) muestra los elementos de menú en sus estados predeterminados hasta que se carga el VSPackage. Posteriormente, el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método se llama para habilitar o deshabilitar elementos de menú.  
  
 Un VSPackage puede establecer una clave del registro para que el VSPackage se cargará automáticamente según un contexto de interfaz de usuario de comandos, aunque normalmente control un origen de VSPackage debe cargar a petición en lugar de simplemente cambiar a un determinado contexto de interfaz de usuario. Para obtener más información sobre la **AutoLoadPackages** registro clave, consulte [administrar VSPackages](../../extensibility/managing-vspackages.md).  
  
## <a name="vspackage-ui"></a>Interfaz de usuario de VSPackage  
 Un paquete de control de código fuente se implementa como un paquete VSPackage y no usa ninguna interfaz de usuario de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Cada control de código fuente VSPackage debe especificar sus propios elementos de interfaz de usuario como elementos de menú, grupos de menús, ventanas de herramientas, las barras de herramientas y cualquier interfaz de usuario necesario para establecer las opciones específicas para el VSPackage de control de código fuente. Estos elementos de interfaz de usuario pueden habilitarse de forma estática o dinámica. Elementos de interfaz de usuario estáticos se definen en un *.vsct* de archivos y se muestran si se carga el VSPackage o no. Elementos de interfaz de usuario dinámicos pueden verse según un contexto de interfaz de usuario de ese comando concreto, como <xref:EnvDTE.Constants.vsContextNoSolution>, o como resultado de una llamada a la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método. La visibilidad de los elementos de interfaz de usuario dinámicas cumple con la estrategia de carga retrasada de VSPackages.  
  
## <a name="ui-constraints-on-source-control-vspackages"></a>Restricciones de interfaz de usuario en los VSPackages de control de código fuente  
 Dado que no se puede quitar el paquete VSPackage de control de código fuente desde el IDE después de cargarlo, VSPackage debe poder entrar en un estado inactivo. Cuando un paquete VSPackage recibe notificación de que ya no está activo, el VSPackage deshabilita su interfaz de usuario y omite cualquier interacción externa del IDE. Implementación de VSPackage de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método debería ocultar comandos cuando el paquete de VS no está activa.  
  
 Cada control de código fuente que VSPackage debe implementar la `IVsSccProvider` interfaz. Dos métodos en la interfaz, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>, debe ser implementada por el VSPackage.  
  
 El control de código fuente VSPackage podrían haberse suscrito a diversos eventos IDE, que se implementan mediante la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>, y así sucesivamente. Además, el VSPackage puede haber implementado las interfaces de devolución de llamada de registro habilitados, como el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>. Estas interfaces todos se deben omitir cuando está inactivo.  
  
 La siguiente lista muestra las interfaces que se ve afectadas por el estado activo de un VSPackage de control de código fuente:  
  
- Realizar un seguimiento de eventos de documentos del proyecto.  
  
- Eventos de la solución.  
  
- Interfaces de persistencia de solución. Cuando esté inactivo, no deben escribir paquetes en *.sln* y *.suo* archivos.  
  
- Extensores de propiedad.  
  
  Necesario <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, y también cualquier interfaces opcionales asociadas con el control de código fuente, no se llama cuando el control de código fuente VSPackage está inactivo.  
  
  Cuando el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] empieza a IDE, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] establece el contexto de interfaz de usuario de comandos para el identificador del control de origen predeterminada Id. de paquete VSPackage actual Esto hace que la interfaz de usuario estática del control de origen activo VSPackage que aparezca en el IDE sin tener que cargar realmente el VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pone en pausa para que el VSPackage registrar con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> antes de que realice cualquier llamada a VSPackage.  
  
  La tabla siguiente describe los detalles específicos acerca de cómo los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE oculta los elementos de interfaz de usuario diferentes.  
  
| Elemento de interfaz de usuario | Descripción |
| - | - |
| Menús y barras de herramientas | El paquete de control de código fuente debe establecer los Estados de visibilidad iniciales de menú y barra de herramientas en el identificador del paquete de control de código fuente en el [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) sección de la *.vsct* archivo. Esto permite la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE para establecer el estado de los elementos de menú correctamente sin tener que cargar el VSPackage y llamar a una implementación de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método. |
| Ventanas de herramientas | El control de código fuente VSPackage oculta las ventanas de herramienta que posee cuando queda inactiva. |
| Páginas de opciones de control de código fuente específico de VSPackage | La clave del registro **HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts** permite un VSPackage establece los contextos en los que requiere que sus páginas de opciones que se mostrará. Una entrada del registro bajo esta clave tiene que crearse mediante el servicio Id. (SID) del servicio de control de código fuente y le asigna un valor DWORD de 1. Cada vez que un evento de interfaz de usuario produce en un contexto de VSPackage esté registrado con el control de código fuente, se llamará el VSPackage si está activa. |
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>   
 <xref:EnvDTE.Constants.vsContextNoSolution>   
 [Administrar los paquetes VSPackage](../../extensibility/managing-vspackages.md)