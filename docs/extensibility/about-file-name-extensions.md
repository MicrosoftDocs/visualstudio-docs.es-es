---
title: Acerca de las extensiones de nombre de archivo | Microsoft Docs
description: Obtenga información sobre cómo registrar las extensiones de nombre de archivo para VSPackages y asociarlas a una versión específica de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f38bee1b62340f7d557ac2e5190fc5c48d9268fe
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060151"
---
# <a name="about-file-name-extensions"></a>Acerca de las extensiones de nombre de archivo
Cuando se registra una extensión de archivo de un VSPackage, se asocia a una versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Esto es importante si hay más de una versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] instalada en un equipo.

 Las extensiones de archivo para VSPackages se registran en **HKEY_CLASSES_ROOT** clave con un valor predeterminado que apunta al identificador de programación (ProgID) asociado.

 En el ejemplo siguiente se muestra la información de registro de la extensión de archivo *. vcproj* :

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)=" VisualStudio.vcproj.8.0"
```

 Los archivos asociados a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] deben tener un ProgID con versión, como `VisualStudio.vcproj.8.0` . Un ProgID con versión permite instalaciones en paralelo del producto para mantener asociaciones de extensión de archivo entre versiones del producto. Un ProgID específico de la versión también le permite usar verbos estándar, como abrir, editar, etc., sin la preocupación de sobrescribir o sobrescribir por otras aplicaciones o versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

 En ciertos casos, no se debe cambiar el ProgID asociado a una extensión de archivo. Por ejemplo, el ProgID para la extensión de archivo *. htm* (ProgID = Htmlfile) está codificado de forma rígida en varios lugares del sistema operativo y es muy conocido y se usa en asociación con los archivos *. htm* y *. html* .

## <a name="see-also"></a>Consulte también
- [Registrar las extensiones de nombre de archivo para implementaciones en paralelo](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Especificar controladores de archivos para las extensiones de nombre de archivo](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
