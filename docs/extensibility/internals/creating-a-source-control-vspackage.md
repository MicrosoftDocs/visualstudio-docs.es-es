---
title: Creación de un VSPackage de Control de código fuente | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0d9513410aa3bb4773629846abbd70159ec6aa77
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499743"
---
# <a name="create-a-source-control-vspackage"></a>Crear un VSPackage de control de código fuente
Esta documentación incluye vínculos a información general de arquitectura de un paquete de control de código fuente integrado con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], la API que se define mediante las interfaces que se va a implementarse y los servicios que se va a consumir y un ejemplo que ilustra un origen simple controlar la implementación del paquete.  
  
 Con un VSPackage de control de código fuente, puede crear una ruta de acceso de la integración profunda para el control de código fuente para integrarse con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Permite que el paquete omitir el control de código fuente predeterminada hospedada por la interfaz de usuario [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], responder a las solicitudes de control de código fuente del sistema del proyecto e interactuar con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] componentes como **el Explorador de soluciones**. El [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] faculta a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] asociados con un mecanismo para crear un VSPackage que se puede integrar con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mediante un modelo de servicio.  
  
## <a name="in-this-section"></a>En esta sección  
 [Introducción](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 Describe el paquete de control de código fuente, que es una alternativa más avanzada para el control de código fuente para implementar características de control de código fuente en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Arquitectura](../../extensibility/internals/source-control-vspackage-architecture.md)  
 Presenta un diagrama y se explican los componentes de un paquete de control de código fuente.  
  
 [Características](../../extensibility/internals/source-control-vspackage-features.md)  
 Describe las distintas características de un paquete de control de código fuente.  
  
 [Elementos de diseño](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 Describe la estructura de VSPackage debe implementar un paquete de control de código fuente para la integración profunda.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Crear un control de código fuente complemento](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Describe cómo crear un complemento de control de origen que proporciona funcionalidad de control de código fuente en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaz de usuario de control de código fuente (UI).  
  
 [Control de código fuente](../../extensibility/internals/source-control.md)  
 Describe las opciones para implementar el control de código fuente como una característica integrada de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].
