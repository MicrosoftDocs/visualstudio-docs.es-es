---
title: Registrar las extensiones de nombre de archivo para las implementaciones en paralelo | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0e80aa90c5fcb6d223e63df6ed740e0295dd3adf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47582459"
---
# <a name="registering-file-name-extensions-for-side-by-side-deployments"></a>Registro de extensiones de nombre de archivo para implementaciones en paralelo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [registrar extensiones de nombre de archivo para las implementaciones de Side-By-Side](https://docs.microsoft.com/visualstudio/extensibility/registering-file-name-extensions-for-side-by-side-deployments).  
  
Para los paquetes VSPackage implementados en un entorno en paralelo, debe registrar las extensiones de nombre de archivo para asociar los archivos con la versión correcta de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. A menos que use una extensión de nombre de archivo específicos de la versión, el registro permite a los usuarios abrir el proyecto y archivos de proyecto elemento en la versión adecuada de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="in-this-section"></a>En esta sección  
 [Acerca de las extensiones de nombre de archivo](../extensibility/about-file-name-extensions.md)  
 Describe cómo se registran las extensiones de nombre de archivo.  
  
 [Especificación de controladores de archivo para extensiones de nombre de archivo](../extensibility/specifying-file-handlers-for-file-name-extensions.md)  
 Proporciona información sobre cómo registrar las aplicaciones que se pueden abrir, edit y así sucesivamente, una extensión de nombre de archivo determinado.  
  
 [Registro de verbos para extensiones de nombre de archivo](../extensibility/registering-verbs-for-file-name-extensions.md)  
 Describe cómo registrar los verbos.  
  
 [Administración de asociaciones de archivos en paralelo](../extensibility/managing-side-by-side-file-associations.md)  
 Describe cómo controlar las instalaciones en paralelo en el que una versión determinada de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] debe invocarse para abrir un archivo.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Compatibilidad con varias versiones de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)  
 Describe problemas relacionados con varias versiones de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y su VSPackage durante el desarrollo e implementación a los usuarios finales.

