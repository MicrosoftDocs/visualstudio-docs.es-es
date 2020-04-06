---
title: Acerca de las extensiones de nombre de archivo ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03e07ec233ef975441a1f10507f0db872051558f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740346"
---
# <a name="about-file-name-extensions"></a>Acerca de las extensiones de nombre de archivo
Cuando se registra una extensión de archivo de un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSPackage, se asocia a una versión de . Esto es importante si hay [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] más de una versión instalada en un equipo.

 Las extensiones de archivo para VSPackages se registran en **HKEY_CLASSES_ROOT** clave con un valor predeterminado que apunta al identificador de programación asociado (ProgID).

 En el ejemplo siguiente se muestra información de registro para la extensión de archivo *.vcproj:*

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)=" VisualStudio.vcproj.8.0"
```

 Los archivos [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] asociados deben tener un ProgID versionado, como `VisualStudio.vcproj.8.0`. Un ProgID versionado permite que las instalaciones en paralelo del producto mantengan las asociaciones de extensión de archivo entre las versiones del producto. Un ProgID específico de la versión también le permite utilizar verbos estándar, como abrir, editar, etc., sin la preocupación de sobrescribir o ser sobrescrito por otras aplicaciones o versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

 En algunos casos, el ProgID asociado con una extensión de archivo no debe cambiarse. Por ejemplo, el ProgID para la extensión de archivo *.htm* (progid - htmlfile) está codificado de forma rígida en varios lugares del sistema operativo y es ampliamente conocido y utilizado en asociación con archivos *.htm* y *.html.*

## <a name="see-also"></a>Vea también
- [Registrar extensiones de nombre de archivo para implementaciones en paralelo](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Especificar controladores de archivos para extensiones de nombre de archivo](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
