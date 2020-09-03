---
title: Crear un VSPackage de control de código fuente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2b1516cf358a4488ff02e650f6c703a1761a94a2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196956"
---
# <a name="creating-a-source-control-vspackage"></a>Creación de un VSPackage de control de código fuente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En esta documentación se incluyen vínculos a información general sobre la arquitectura de un paquete de control de código fuente integrado con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , la API que se define en las interfaces que se van a implementar y los servicios que se van a consumir, y un ejemplo que muestra una implementación simple de un paquete de control de código fuente.  
  
 Con un VSPackage de control de código fuente, puede crear una ruta de acceso de integración profunda para que el control de código fuente se integre con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Permite que el paquete omita la interfaz de usuario de control de código fuente predeterminada hospedada por [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , responda a las solicitudes de control de código fuente del sistema del proyecto e interactúe con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] los componentes como **Explorador de soluciones**. [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]Permite a los [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] asociados tener un mecanismo para crear un VSPackage que se puede integrar con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] el uso de un modelo de servicio.  
  
## <a name="in-this-section"></a>En esta sección  
 [Introducción](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 Describe el paquete de control de código fuente, que es una alternativa más avanzada al complemento de control de código fuente para implementar características de control de código fuente en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Architecture](../../extensibility/internals/source-control-vspackage-architecture.md)  
 Presenta un diagrama y explica los componentes de un paquete de control de código fuente.  
  
 [Características](../../extensibility/internals/source-control-vspackage-features.md)  
 Describe las distintas características de un paquete de control de código fuente.  
  
 [Elementos de diseño](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 Describe la estructura del VSPackage que un paquete de control de código fuente debe implementar para la integración profunda.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Creación de un complemento de control de código fuente](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Describe cómo crear un complemento de control de código fuente que proporciona la funcionalidad de control de código fuente en la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interfaz de usuario (UI) del control de código fuente.  
  
 [Control de código fuente](../../extensibility/internals/source-control.md)  
 Describe las opciones para implementar el control de código fuente como una característica integrada de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .
