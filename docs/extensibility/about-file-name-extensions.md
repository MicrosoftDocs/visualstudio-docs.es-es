---
title: Acerca de las extensiones de nombre de archivo | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4aba03fd68fc5e0e68dbf13887de0c25094fa951
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="about-file-name-extensions"></a>Acerca de las extensiones de nombre de archivo
Al registrar una extensión de archivo de un paquete VSPackage, se asocia con una versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Esto es importante si más de una versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] está instalado en un equipo.  
  
 Extensiones de archivo para VSPackages están registradas en la clave HKEY_CLASSES_ROOT con un valor predeterminado que señala el identificador de programación (ProgID) asociado.  
  
 El siguiente es un ejemplo de la información de registro para la extensión de archivo .vcproj:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 Archivos asociados con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] deben tener un ProgID con control de versiones, como `VisualStudio.vcproj.8.0`, para permitir que las instalaciones en paralelo del producto para mantener las asociaciones de extensión de archivo entre las versiones del producto. Un ProgID específico de la versión también le permite usar los verbos estándar, como abrir, editar y así sucesivamente, sin preocuparse de sobrescribir o sobrescriba otras aplicaciones o las versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 En algunos casos, no debe cambiarse el ProgID asociado con una extensión de archivo. Por ejemplo, el ProgID de la extensión de archivo .htm (progid = archivo HTML) está codificado en un número de posiciones en el sistema operativo, y es muy conocida y se usa en asociación con archivos .htm y .html.  
  
## <a name="see-also"></a>Vea también  
 [Registrar las extensiones de nombre de archivo para las implementaciones en paralelo](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Especificación de controladores de archivo para extensiones de nombre de archivo](../extensibility/specifying-file-handlers-for-file-name-extensions.md)