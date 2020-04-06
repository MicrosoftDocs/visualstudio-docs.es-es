---
title: Interfaz de usuario personalizada (VSPackage de control de código fuente) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6ef807cef17a6ca3cddfee05ba57ace27e34a9e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708927"
---
# <a name="custom-user-interface-source-control-vspackage"></a>Interfaz de usuario personalizada (control de código fuente VSPackage)
Un VSPackage declara sus elementos de menú y sus estados predeterminados a través de la tabla de comandos de Visual Studio (*.vsct*) archivo. El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno de desarrollo integrado (IDE) muestra los elementos de menú en sus estados predeterminados hasta que se carga el VSPackage. Posteriormente, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> se llama al método para habilitar o deshabilitar los elementos de menú.

 Un VSPackage puede establecer una clave del Registro para que el VSPackage se puede cargar automáticamente en función de un contexto de interfaz de usuario de comando (UI), aunque normalmente un control de código fuente VSPackage debe cargar a petición en lugar de simplemente cambiar a un contexto de interfaz de usuario determinado. Para obtener más información acerca de la clave del Registro **AutoLoadPackages,** vea [Administrar VSPackages](../../extensibility/managing-vspackages.md).

## <a name="vspackage-ui"></a>Interfaz de usuario de VSPackage
 Un paquete de control de código fuente se implementa [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]como un VSPackage y no usa ninguna interfaz de usuario de . Cada control de código fuente VSPackage debe especificar sus propios elementos de interfaz de usuario, como elementos de menú, grupos de menús, ventanas de herramientas, barras de herramientas y cualquier interfaz de usuario necesaria para establecer opciones específicas para el control de código fuente VSPackage. Estos elementos de interfaz de usuario se pueden habilitar estática o dinámicamente. Elementos de interfaz de usuario estáticos se definen en un archivo *.vsct* y se muestran si el VSPackage está cargado o no. Los elementos dinámicos de la <xref:EnvDTE.Constants.vsContextNoSolution> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> interfaz de usuario pueden estar visibles en función de un contexto de interfaz de usuario de comando determinado, como , o como resultado de una llamada al método. La visibilidad de los elementos dinámicos de la interfaz de usuario cumple con la estrategia para la carga retrasada de VSPackages.

## <a name="ui-constraints-on-source-control-vspackages"></a>Restricciones de interfaz de usuario en VSPackages de control de código fuente
 Dado que el control de código fuente VSPackage no se puede quitar del IDE después de que se carga, el VSPackage debe ser capaz de escribir un estado inactivo. Cuando un VSPackage recibe una notificación de que ya no está activo, el VSPackage deshabilita su interfaz de usuario e ignora cualquier interacción IDE externa. La implementación del VSPackage del <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método debe ocultar comandos cuando el VSPackage no está activo.

 Cada control de código `IVsSccProvider` fuente VSPackage debe implementar la interfaz. El VSPackage debe <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>implementar dos métodos en la interfaz y , .

 El control de código fuente VSPackage puede haberse suscrito a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>varios eventos IDE, que se implementan mediante el , , etc. Además, el VSPackage puede haber implementado interfaces de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>devolución de llamada habilitadas para el registro, como el archivo . Estas interfaces deben ser ignoradas cuando están inactivas.

 La lista siguiente muestra las interfaces afectadas por el estado activo de un control de código fuente VSPackage:

- Realizar un seguimiento de los eventos de documentos del proyecto.

- Eventos de solución.

- Interfaces de persistencia de soluciones. Cuando está inactivo, los paquetes no deben escribir en archivos *.sln* y *.suo.*

- Extensores de propiedad.

  El <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> necesario <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>y , y también las interfaces opcionales asociadas con el control de código fuente, no se llama cuando el control de código fuente VSPackage está inactivo.

  Cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se inicia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el IDE, establece el contexto de la interfaz de usuario del comando en el identificador del identificador de VSPackage del control de código fuente predeterminado actual. Esto hace que la interfaz de usuario estática del control de código fuente activo VSPackage aparezca en el IDE sin cargar realmente el VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]pausas para el VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> registrarse a través de la antes de realizar cualquier llamada al VSPackage.

  En la tabla siguiente se [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] describen detalles específicos sobre cómo el IDE oculta diferentes elementos de interfaz de usuario.

| Elemento de la interfaz de usuario | Descripción |
| - | - |
| Menús y barras de herramientas | El paquete de control de código fuente debe establecer los estados de visibilidad del menú y la barra de herramientas iniciales en el identificador del paquete de control de código fuente en la sección [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) del archivo *.vsct.* Esto permite [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que el IDE para establecer el estado de los elementos <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> de menú correctamente sin cargar el VSPackage y llamar a una implementación del método. |
| Ventanas de herramientas | El control de código fuente VSPackage oculta las ventanas de herramientas que posee cuando se vuelve inactiva. |
| Páginas de opciones específicas de VSPackage de control de código fuente | La clave del Registro **HKLM-SOFTWARE-Microsoft-VisualStudio-X.Y-ToolsOptionsPages-VisibilityCmdUIContexts** permite a un VSPackage establecer los contextos en los que requiere que se muestren sus páginas de opciones. Una entrada de registro bajo esta clave tendría que crearse mediante el identificador de servicio (SID) del servicio de control de código fuente y asignarle un valor DWORD de 1. Siempre que se produce un evento de interfaz de usuario en un contexto con el que se registra el control de código fuente VSPackage, se llamará al VSPackage si está activo. |

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>
- <xref:EnvDTE.Constants.vsContextNoSolution>
- [Administración de VSPackages](../../extensibility/managing-vspackages.md)
