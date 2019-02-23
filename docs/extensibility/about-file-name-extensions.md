---
title: Acerca de las extensiones de nombre de archivo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9998a8a07995f866b1833736b96e2884c5cba091
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56678402"
---
# <a name="about-file-name-extensions"></a>Acerca de las extensiones de nombre de archivo
Al registrar una extensión de archivo de un paquete VSPackage, asocia con una versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Esto es importante si más de una versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] está instalado en un equipo.

 Extensiones de archivo para paquetes VSPackage registradas bajo **HKEY_CLASSES_ROOT** clave con un valor predeterminado que señala el identificador de programación (ProgID) asociado.

 El ejemplo siguiente muestra la información de registro para el *.vcproj* la extensión de archivo:

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)=" VisualStudio.vcproj.8.0"
```

 Los archivos asociados con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] deben tener un ProgID con control de versiones, como `VisualStudio.vcproj.8.0`. Un ProgID con control de versiones permite instalaciones en paralelo del producto para mantener las asociaciones de extensión de archivo entre las versiones de producto. Un ProgID específico de la versión también permite usar los verbos estándar, como abrir, editar y así sucesivamente, sin preocuparse de sobrescribir ni ser sobrescrito por otras aplicaciones o las versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

 En algunos casos, no se debe cambiar el identificador de programa asociado con una extensión de archivo. Por ejemplo, el ProgID de la *.htm* la extensión de archivo (Id. de programa = archivo HTML) está codificado de forma rígida en varios lugares en el sistema operativo, y es muy conocida y se usa en asociación con *.htm* y *.html* archivos.

## <a name="see-also"></a>Vea también
- [Registrar extensiones de nombre de archivo para las implementaciones en paralelo](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Especifique los controladores de archivo de extensiones de nombre de archivo](../extensibility/specifying-file-handlers-for-file-name-extensions.md)