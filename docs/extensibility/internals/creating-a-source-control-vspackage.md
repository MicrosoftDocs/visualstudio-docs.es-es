---
title: "Crear un VSPackage del Control de c&#243;digo fuente | Microsoft Docs"
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
  - "control de código fuente [Visual Studio SDK], crear paquetes de control de código fuente"
  - "paquetes de control de código fuente"
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
caps.latest.revision: 23
caps.handback.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
---
# Crear un VSPackage del Control de c&#243;digo fuente
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Esta documentación incluye vínculos a información general de la arquitectura de un paquete de control de código fuente integrado con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], API definido por las interfaces que se van a implementar y los servicios que se consumirán, y un ejemplo que muestra una implementación sencilla de paquete de control de código fuente.  
  
 Con un control de código fuente VSPackage, puede crear una ruta conocen la integración del control de código fuente integrado en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Permite al paquete para omitir la interfaz de usuario predeterminada del control de origen hospedada por [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], para responder a las solicitudes de control de código fuente del sistema del proyecto, e interactuar con los componentes de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] como **Explorador de soluciones**.  [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] autoriza a socios de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] con un mecanismo para crear un Paquete que pueda integrar con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mediante un modelo de servicio.  
  
## En esta sección  
 [Introducción](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 Describe el paquete de control de código fuente, que es una alternativa más avanzado al complemento de control de código fuente para implementar características de control de código fuente en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Arquitectura](../../extensibility/internals/source-control-vspackage-architecture.md)  
 Muestra un diagrama y explica los componentes de un paquete de control de código fuente.  
  
 [Características](../../extensibility/internals/source-control-vspackage-features.md)  
 Describe las distintas características de un paquete de control de código fuente.  
  
 [Elementos de diseño](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 Describe la estructura del Paquete que un paquete de control de código fuente debe implementar para la integración profunda.  
  
## Secciones relacionadas  
 [Creación de un Control de origen de complemento](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Describe cómo crear un complemento de control de código fuente esa funcionalidad de control de código fuente de las fuentes en la interfaz de usuario del control de código fuente de \(UI\) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  
  
 [Control de código fuente](../../extensibility/internals/source-control.md)  
 Describe las opciones para implementar el control de código fuente como característica integrada de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].