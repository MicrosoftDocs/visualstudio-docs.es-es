---
title: Creación de un VSPackage de Control de código fuente | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d7d897e8aeaf140048695a14d552ae5c5ab200a1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49220030"
---
# <a name="creating-a-source-control-vspackage"></a>Creación de un VSPackage de control de código fuente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Esta documentación incluye vínculos a información general de arquitectura de un paquete de control de código fuente integrado con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], la API que se define mediante las interfaces que se va a implementarse y los servicios que se va a consumir y un ejemplo que ilustra un origen simple controlar la implementación del paquete.  
  
 Con un VSPackage de control de código fuente, puede crear una ruta de acceso de la integración profunda para el control de código fuente para integrarse con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Permite que el paquete omitir el control de código fuente predeterminada hospedada por la interfaz de usuario [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], responder a las solicitudes de control de código fuente del sistema del proyecto e interactuar con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] componentes como **el Explorador de soluciones**. El [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] faculta a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] asociados con un mecanismo para crear un VSPackage que se puede integrar con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mediante un modelo de servicio.  
  
## <a name="in-this-section"></a>En esta sección  
 [Introducción](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 Describe el paquete de control de código fuente, que es una alternativa más avanzada para el control de código fuente para implementar características de control de código fuente en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Arquitectura](../../extensibility/internals/source-control-vspackage-architecture.md)  
 Presenta un diagrama y se explican los componentes de un paquete de control de código fuente.  
  
 [Características](../../extensibility/internals/source-control-vspackage-features.md)  
 Describe las distintas características de un paquete de control de código fuente.  
  
 [Elementos de diseño](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 Describe la estructura de VSPackage debe implementar un paquete de control de código fuente para la integración profunda.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Creación de un complemento de control de código fuente](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Describe cómo crear un complemento de control de origen que proporciona funcionalidad de control de código fuente en el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interfaz de usuario de control de código fuente (UI).  
  
 [Control de código fuente](../../extensibility/internals/source-control.md)  
 Describe las opciones para implementar el control de código fuente como una característica integrada de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

