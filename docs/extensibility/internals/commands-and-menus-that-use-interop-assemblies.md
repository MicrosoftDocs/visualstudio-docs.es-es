---
title: "Comandos y men&#250;s que utilizan ensamblados de interoperabilidad | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "menús, mediante ensamblados de interoperabilidad"
  - "ensamblados de interoperabilidad, mediante comandos y menús"
  - "comandos, controlar el uso de ensamblados de interoperabilidad"
  - "control con ensamblados de interoperabilidad de comandos"
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Comandos y men&#250;s que utilizan ensamblados de interoperabilidad
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un VSPackage que implementa los comandos de menú y barra de herramientas mediante el uso de ensamblados de interoperabilidad debe:  
  
-   Informar a la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado \(IDE\) acerca de los comandos que admite y si están habilitadas actualmente.  
  
-   Cumplir las reglas \(contrato\) para controlar los comandos.  
  
-   Implementar explícitamente la gestión de comandos utilizando el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaz.  
  
 A continuación describe cómo realizar estas tareas.  
  
## En esta sección  
 [Determinar el estado de comandos mediante el uso de ensamblados de interoperabilidad](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 Describe cómo un VSPackage le notifique sobre los comandos que admite y si están habilitadas actualmente.  
  
 [Comando de contratos en los ensamblados de interoperabilidad](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 Proporciona una definición del contrato de comando básico usado por todos los VSPackages implementar comandos con ensamblados de interoperabilidad  
  
 [Implementación](../../extensibility/internals/command-implementation.md)  
 Proporciona una visión general de cómo un VSPackage implementa un comando.  
  
 [Registrar controladores de comandos de ensamblado de interoperabilidad](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 Describe las entradas del registro necesarias para notificar el IDE que un paquete VSPackage proporciona un controlador de comandos.  
  
## Secciones relacionadas  
 [Disponibilidad](../../extensibility/internals/command-availability.md)  
 Describe los criterios que se usan por el IDE para determinar qué comandos VSPackage están disponibles y qué objeto encarga de administrarlos.  
  
 [Cómo VSPackages agregar elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Proporciona detalles sobre cómo crear una interfaz de usuario que utiliza [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] compatibilidad de comandos.  
  
 [Enrutamiento de comandos en VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)  
 Información general sobre el proceso que se utiliza para relacionar un objeto con la solicitud de comando correcto.