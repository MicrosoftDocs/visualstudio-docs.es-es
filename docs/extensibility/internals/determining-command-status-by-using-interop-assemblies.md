---
title: Determinar el estado del comando mediante el uso de ensamblados de interoperabilidad | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4989910fdec968a4a05e2459e6625ee2c15fd9a4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128182"
---
# <a name="determining-command-status-by-using-interop-assemblies"></a>Determinar el estado del comando mediante el uso de ensamblados de interoperabilidad
Un VSPackage debe realizar un seguimiento del estado de los comandos que puede controlar. Cuando un comando que se controla en el paquete de VS deja de estar habilitado o deshabilitado, no puede determinar el entorno. Es responsabilidad del paquete de VS para informar del entorno acerca de los Estados de comando, por ejemplo, el estado de general comandos como **cortar**, **copia**, y **pegar**.  
  
## <a name="status-notification-sources"></a>Orígenes de notificación de estado  
 El entorno recibe información sobre los comandos a través de los VSPackages <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método, que forma parte de la implementación de VSPackage de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz. El entorno llama el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método de VSPackage bajo dos condiciones:  
  
-   Cuando un usuario abre un menú principal o un menú contextual (haciendo clic en), el entorno se ejecuta el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método en todos los comandos de menú para determinar su estado.  
  
-   Cuando el VSPackage solicita que el entorno de actualizar la interfaz de usuario (IU) actual. Esto se produce cuando los comandos que están visibles para el usuario, como el **cortar**, **copia**, y **pegar** agrupar en la barra de herramientas estándar, están habilitados y deshabilitados en respuesta a las acciones del usuario y el contexto.  
  
 Puesto que el shell hospeda varias VSPackages, inaceptablemente podría degradar el rendimiento del shell si se requiere para sondear cada paquete VSPackage para determinar el estado del comando. En su lugar, el VSPackage activamente debe notificar el entorno cuando cambia su interfaz de usuario en el momento del cambio. Para obtener más información sobre la notificación de actualización, vea [actualizar la interfaz de usuario](../../extensibility/updating-the-user-interface.md).  
  
## <a name="status-notification-failure"></a>Error de notificación de estado  
 Error del paquete de VS para notificar el entorno de un comando de cambio de estado puede colocar la interfaz de usuario en un estado incoherente. Recuerde que cualquiera de los comandos de menú contextual o del menú puede colocarse en una barra de herramientas por el usuario. Por lo tanto, actualizar la interfaz de usuario solo cuando se abre un menú contextual o del menú no es suficiente.  
  
## <a name="see-also"></a>Vea también  
 [¿Cómo VSPackages agregar elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implementación](../../extensibility/internals/command-implementation.md)