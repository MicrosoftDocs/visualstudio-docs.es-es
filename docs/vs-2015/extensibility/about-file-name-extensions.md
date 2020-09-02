---
title: Acerca de las extensiones de nombre de archivo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 866a30279ca2c79f4a490a040f76bc3a86c6a6e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148031"
---
# <a name="about-file-name-extensions"></a>Acerca de las extensiones de nombre de archivo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cuando se registra una extensión de archivo de un VSPackage, se asocia a una versión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Esto es importante si hay más de una versión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] instalada en un equipo.  
  
 Las extensiones de archivo para VSPackages se registran en HKEY_CLASSES_ROOT clave con un valor predeterminado que apunta al identificador de programación (ProgID) asociado.  
  
 El siguiente es un ejemplo de la información de registro de la extensión de archivo. vcproj:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 Los archivos asociados a [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] deben tener un ProgID con versión, como `VisualStudio.vcproj.8.0` , para permitir instalaciones en paralelo del producto con el fin de mantener asociaciones de extensión de archivo entre versiones del producto. Un ProgID específico de la versión también le permite usar verbos estándar, como abrir, editar, etc., sin la preocupación de sobrescribir o sobrescribir por otras aplicaciones o versiones de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 En ciertos casos, no se debe cambiar el ProgID asociado a una extensión de archivo. Por ejemplo, el ProgID para la extensión de archivo. htm (ProgID = Htmlfile) está codificado de forma rígida en varios lugares del sistema operativo y es muy conocido y se usa en asociación con los archivos. htm y. html.  
  
## <a name="see-also"></a>Consulte también  
 [Registro de extensiones de nombre de archivo para implementaciones en paralelo](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Especificación de controladores de archivo para extensiones de nombre de archivo](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
