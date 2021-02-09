---
title: Interfaz de usuario personalizada (VSPackage de control de código fuente) | Microsoft Docs
description: Obtenga información sobre cómo crear una interfaz de usuario (UI) personalizada en Visual Studio mediante un VSPackage de control de código fuente para especificar los elementos de la interfaz de usuario.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 97c82254516c78a3aff9884e91e44adc45b95981
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902988"
---
# <a name="custom-user-interface-source-control-vspackage"></a>Interfaz de usuario personalizada (VSPackage de control de código fuente)
Un VSPackage declara sus elementos de menú y sus Estados predeterminados a través del archivo de tabla de comandos de Visual Studio (*. Vsct*). El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno de desarrollo integrado (IDE) muestra los elementos de menú en sus Estados predeterminados hasta que se carga el VSPackage. Posteriormente, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> se llama al método para habilitar o deshabilitar elementos de menú.

 Un VSPackage puede establecer una clave del registro para que el VSPackage pueda cargarse automáticamente según un contexto de interfaz de usuario de comandos, aunque normalmente un VSPackage de control de código fuente debe cargarse a petición en lugar de simplemente cambiar a un contexto de interfaz de usuario determinado. Para obtener más información acerca de la clave del registro **AutoLoadPackages** , vea [administrar VSPackages](../../extensibility/managing-vspackages.md).

## <a name="vspackage-ui"></a>Interfaz de usuario de VSPackage
 Un paquete de control de código fuente se implementa como un VSPackage y no usa ninguna interfaz de usuario de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Cada VSPackage de control de código fuente debe especificar sus propios elementos de interfaz de usuario, como elementos de menú, grupos de menús, ventanas de herramientas, barras de herramientas y cualquier interfaz de usuario necesaria para establecer opciones específicas del VSPackage de control de código fuente. Estos elementos de la interfaz de usuario se pueden habilitar estática o dinámicamente. Los elementos de interfaz de usuario estáticos se definen en un archivo *. Vsct* y se muestran si el VSPackage está cargado o no. Los elementos de interfaz de usuario dinámicos pueden ser visibles dependiendo de un contexto de interfaz de usuario de comando concreto, como <xref:EnvDTE.Constants.vsContextNoSolution> , o como resultado de una llamada al <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método. La visibilidad de los elementos de la interfaz de usuario dinámica es compatible con la estrategia de carga diferida de VSPackages.

## <a name="ui-constraints-on-source-control-vspackages"></a>Restricciones de interfaz de usuario en VSPackages de control de código fuente
 Dado que el VSPackage de control de código fuente no se puede quitar del IDE una vez cargado, el VSPackage debe ser capaz de entrar en un estado inactivo. Cuando un VSPackage recibe una notificación de que ya no está activa, el VSPackage deshabilita su interfaz de usuario y omite cualquier interacción de IDE externa. La implementación del VSPackage del <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método debe ocultar los comandos cuando el VSPackage no está activo.

 Cada VSPackage de control de código fuente debe implementar la `IVsSccProvider` interfaz. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A>El VSPackage debe implementar dos métodos en la interfaz, y <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> .

 El VSPackage de control de código fuente puede haberse suscrito a varios eventos IDE, que se implementan mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> , <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> , etc. Además, el VSPackage puede haber implementado interfaces de devolución de llamada habilitadas para el registro, como <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> . Se deben omitir todas estas interfaces cuando están inactivas.

 En la siguiente lista se muestran las interfaces afectadas por el estado activo de un VSPackage de control de código fuente:

- Seguimiento de eventos de documentos de proyecto.

- Eventos de la solución.

- Interfaces de persistencia de soluciones. Cuando está inactivo, los paquetes no deben escribir en los archivos *. sln* y *. suo* .

- Extensores de propiedad.

  <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> No se llama a los necesarios y, y también a las interfaces opcionales asociadas al control de código fuente, cuando el VSPackage del control de código fuente está inactivo.

  Cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se inicia el IDE, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] establece el contexto de la interfaz de usuario de comandos en el identificador del ID. de VSPackage del control de código fuente predeterminado actual. Esto hace que la interfaz de usuario estática del VSPackage de control de código fuente activo aparezca en el IDE sin cargar realmente el VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pausa para que el VSPackage se registre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mediante el antes de realizar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> cualquier llamada al VSPackage.

  En la tabla siguiente se describen los detalles específicos sobre cómo el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE oculta distintos elementos de la interfaz de usuario.

| Elemento de interfaz de usuario | Descripción |
| - | - |
| Menús y barras de herramientas | El paquete de control de código fuente debe establecer los Estados de visibilidad de la barra de herramientas y el menú inicial en el identificador del paquete de control de código fuente en la sección [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) del archivo *. Vsct* . Esto permite al [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE establecer el estado de los elementos de menú adecuadamente sin cargar el VSPackage y llamar a una implementación del <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método. |
| Ventanas de herramientas | El VSPackage de control de código fuente oculta las ventanas de herramientas que posee cuando se convierte en inactivas. |
| Páginas de opciones específicas del VSPackage de control de código fuente | La clave del registro **HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts** permite que un paquete VSPackage establezca los contextos en los que es necesario que se muestren sus páginas de opciones. Una entrada del registro con esta clave tendría que crearse mediante el identificador de servicio (SID) del servicio de control de código fuente y asignarle un valor DWORD de 1. Siempre que se produce un evento de interfaz de usuario en un contexto con el que se registra el VSPackage de control de código fuente, se llamará al VSPackage si está activo. |

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>
- <xref:EnvDTE.Constants.vsContextNoSolution>
- [Administración de VSPackages](../../extensibility/managing-vspackages.md)
