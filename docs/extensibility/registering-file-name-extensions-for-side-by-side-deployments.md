---
title: Registrar las extensiones de nombre de archivo para las implementaciones en paralelo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ae7d7307ef12184dcbfc29254ec5cbae9ff55bb8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136315"
---
# <a name="registering-file-name-extensions-for-side-by-side-deployments"></a>Registrar las extensiones de nombre de archivo para las implementaciones en paralelo
Para paquetes VSPackage implementado en un entorno en paralelo, debe registrar las extensiones de nombre de archivo para asociar los archivos de la versión correcta de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. A menos que utilice una extensión de nombre de archivo específico de la versión, el registro permite a los usuarios abrir el proyecto y archivos de proyecto elemento en la versión adecuada de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>En esta sección  
 [Acerca de las extensiones de nombre de archivo](../extensibility/about-file-name-extensions.md)  
 Describe cómo se registran las extensiones de nombre de archivo.  
  
 [Especificación de controladores de archivo para extensiones de nombre de archivo](../extensibility/specifying-file-handlers-for-file-name-extensions.md)  
 Proporciona información sobre cómo registrar las aplicaciones que se pueden abrir, editar y así sucesivamente, una extensión de nombre de archivo en particular.  
  
 [Registro de verbos para extensiones de nombre de archivo](../extensibility/registering-verbs-for-file-name-extensions.md)  
 Describe cómo registrar los verbos.  
  
 [Administración de asociaciones de archivos en paralelo](../extensibility/managing-side-by-side-file-associations.md)  
 Describe cómo controlar las instalaciones en paralelo en el que una versión determinada de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se debe invocar para abrir un archivo.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Compatibilidad con varias versiones de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)  
 Describe los problemas relacionados con varias versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y su VSPackage durante el desarrollo y la implementación a los usuarios finales.