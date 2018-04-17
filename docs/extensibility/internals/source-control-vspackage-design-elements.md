---
title: Elementos de diseño de VSPackage de Control de origen | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eb741a7dc7423c27baed2cd79476239f4e41a170
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="source-control-vspackage-design-elements"></a>Elementos de diseño de VSPackage del Control de código fuente
Los temas de esta sección describen la estructura de control de código fuente VSPackage debe implementar para la integración profunda. También se muestran las interfaces y los servicios que el origen de control VSPackage pueden implementar y las interfaces y los servicios puede usar el control de código fuente VSPackage desde otros [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] modelo y la funcionalidad de control de componentes para admitir su origen.  
  
## <a name="in-this-section"></a>En esta sección  
 [Estructura de VSPackage](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)  
 Define la estructura del control de código fuente VSPackage.  
  
 [Interfaces y servicios relacionados](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)  
 Enumera los interfaces relacionadas con el paquete de control de origen y servicios.  
  
 [Servicios proporcionados](../../extensibility/internals/services-provided-source-control-vspackage.md)  
 Describe el servicio de control de origen proporcionado por el control de código fuente VSPackage.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Creación de un VSPackage de control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md)  
 Describe cómo crear un control de código fuente VSPackage que no solo proporciona funcionalidad de control de código fuente, pero se puede usar para personalizar el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaz de usuario de control de código fuente.