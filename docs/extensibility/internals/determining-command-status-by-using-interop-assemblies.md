---
title: "Determinar el estado de comandos mediante el uso de ensamblados de interoperabilidad | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ensamblados de interoperabilidad, determinar el estado del comando"
  - "control con ensamblados de interoperabilidad, estado de comandos"
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Determinar el estado de comandos mediante el uso de ensamblados de interoperabilidad
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un VSPackage debe mantener un seguimiento del estado de los comandos que puede controlar. El entorno no puede determinar si un comando controlado en el VSPackage se convierte en habilitada o deshabilitado. Es responsabilidad de su paquete VSPackage para informar del entorno acerca de los Estados de comando, por ejemplo, el estado de general de los comandos como **Cortar**, **copia**, y **Pegar**.  
  
## Orígenes de notificación de estado  
 El entorno recibe información sobre los comandos a través de 'VSPackages <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método, que es parte de la implementación de VSPackage de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz. El entorno llama el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método de VSPackage bajo dos condiciones:  
  
-   Cuando un usuario abre un menú principal o un menú contextual \(clic\), el entorno se ejecuta el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método en todos los comandos de menú para determinar su estado.  
  
-   Cuando el paquete VSPackage solicita que el entorno de actualizar la interfaz de usuario \(IU\) actual. Esto ocurre que los comandos que están visibles para el usuario, como el **Cortar**, **copia**, y **Pegar** agrupar en la barra de herramientas estándar, esté habilitada y deshabilitada en respuesta a acciones del usuario y el contexto.  
  
 Puesto que el shell de hosts múltiples VSPackages, inaceptablemente podría degradar el rendimiento del shell si era necesario para sondear cada VSPackage para determinar el estado del comando. En su lugar, el VSPackage debe notificar activamente el entorno cuando cambia su interfaz de usuario en el momento del cambio. Para obtener más información sobre la notificación de actualización, consulte [Actualización de la interfaz de usuario](../../extensibility/updating-the-user-interface.md).  
  
## Error de notificación de estado  
 Error de su paquete VSPackage para notificar el entorno de un comando de cambio de estado puede colocar la interfaz de usuario en un estado incoherente. Recuerde que algunos de los comandos de menú contextual o del menú se pueden colocar en una barra de herramientas por el usuario. Por lo tanto, actualizar la interfaz de usuario sólo cuando se abre un menú contextual o del menú no es suficiente.  
  
## Vea también  
 [Cómo VSPackages agregar elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implementación](../../extensibility/internals/command-implementation.md)