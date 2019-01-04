---
title: Determinar el estado del comando mediante el uso de ensamblados de interoperabilidad | Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 8d3c6a0f74f6f9f684e35c927bafc2ead7c19485
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53967753"
---
# <a name="determine-command-status-by-using-interop-assemblies"></a>Determinar el estado del comando mediante el uso de ensamblados de interoperabilidad
Un VSPackage debe mantener un seguimiento del estado de los comandos que puede controlar. El entorno no puede determinar si un comando que se controla en el VSPackage se convierte en habilitado o deshabilitado. Es responsabilidad del paquete de VS para informar al entorno acerca de los Estados de comando, por ejemplo, el estado de general de los comandos como **cortar**, **copia**, y **pegar**.  
  
## <a name="status-notification-sources"></a>Orígenes de notificación de estado  
 El entorno recibe información acerca de los comandos a través de 'VSPackages <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método, que forma parte de la implementación de VSPackage de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz. El entorno llama a la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método del VSPackage bajo dos condiciones:  
  
- Cuando un usuario abre un menú principal o un menú contextual (haciendo clic), el entorno se ejecuta el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método en todos los comandos de menú para determinar su estado.  
  
- Cuando el VSPackage solicita que el entorno de actualización de la interfaz de usuario (IU) actual. Esta actualización se produce como los comandos que están actualmente visibles para el usuario, como el **cortar**, **copia**, y **pegar** agrupación en la barra de herramientas estándar, se convierten en habilitado y deshabilitado en respuesta a acciones de contexto y el usuario.  
  
  Puesto que el shell hospeda varios VSPackages, inaceptablemente podría degradar el rendimiento del shell si se requiere para sondear cada VSPackage para determinar el estado del comando. En su lugar, el VSPackage debe notificar activamente el entorno cuando cambia su interfaz de usuario en el momento del cambio. Para obtener más información sobre la notificación de actualización, vea [actualizar la interfaz de usuario](../../extensibility/updating-the-user-interface.md).  
  
## <a name="status-notification-failure"></a>Error de notificación de estado  
 Error del paquete de VS para notificar el entorno de un comando de cambio de estado puede colocar la interfaz de usuario en un estado incoherente. Recuerde que cualquiera de los comandos de menú contextual o del menú se pueden colocar en una barra de herramientas por el usuario. Por lo tanto, actualizar la interfaz de usuario solo cuando se abre un menú contextual o del menú no es suficiente.  
  
## <a name="see-also"></a>Vea también  
 [Cómo VSPackages agregar elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implementación](../../extensibility/internals/command-implementation.md)