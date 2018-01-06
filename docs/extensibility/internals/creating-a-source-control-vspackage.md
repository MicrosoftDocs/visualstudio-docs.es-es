---
title: "Crear un VSPackage de Control de código fuente | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c3fac86583126e94bcfaea65a82c7cf923275769
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-source-control-vspackage"></a>Crear un VSPackage de Control de código fuente
Esta documentación incluyen vínculos a información general de arquitectura de un paquete de control de código fuente integrado con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], la API que se define mediante las interfaces que implementará y los servicios que se va a consumir y un ejemplo que muestra un origen simple controlar la implementación del paquete.  
  
 Con un control de código fuente VSPackage, puede crear una ruta de acceso de la integración profunda para el control de código fuente para integrarse con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Hace que el paquete se omitirá el control de código fuente predeterminada IU hospedado por [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], responder a las solicitudes de control de código fuente desde el sistema del proyecto e interactuar con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] componentes como **el Explorador de soluciones**. El [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] atribuye [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se asocia con un mecanismo para crear un VSPackage que se puede integrar con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mediante un modelo de servicio.  
  
## <a name="in-this-section"></a>En esta sección  
 [Introducción](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 Describe el paquete de control de código fuente, que es una alternativa más avanzada para el control de código fuente complemento para implementar características de control de código fuente de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Arquitectura](../../extensibility/internals/source-control-vspackage-architecture.md)  
 Presenta un diagrama y se explican los componentes de un paquete de control de código fuente.  
  
 [Características](../../extensibility/internals/source-control-vspackage-features.md)  
 Describe las distintas características de un paquete de control de código fuente.  
  
 [Elementos de diseño](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 Describe la estructura de VSPackage debe implementar un paquete de control de código fuente para la integración profunda.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Creación de un complemento de control de código fuente](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Describe cómo crear un complemento de control de código fuente que proporciona funcionalidad de control de código fuente de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaz de usuario de control de código fuente (UI).  
  
 [Control de código fuente](../../extensibility/internals/source-control.md)  
 Describe las opciones para implementar el control de código fuente como una característica integrada de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].