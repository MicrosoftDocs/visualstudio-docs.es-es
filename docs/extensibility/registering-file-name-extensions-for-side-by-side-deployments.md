---
title: Registro de extensiones de nombre de archivo para implementaciones en paralelo Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6717625a44b48a25d293f68d01cd9fa3c7c24853
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701548"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>Registrar extensiones de nombre de archivo para implementaciones en paralelo
Para VSPackages implementados en un entorno en paralelo, debe registrar las extensiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]nombre de archivo para asociar los archivos con la versión correcta de . A menos que utilice una extensión de nombre de archivo específica de la versión, el registro permite a los usuarios abrir los archivos de elementos de proyecto y proyecto en la versión adecuada de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="in-this-section"></a>En esta sección
- [Acerca de las extensiones de nombre de archivo](../extensibility/about-file-name-extensions.md) Describe cómo se registran las extensiones de nombre de archivo.

- [Especificar controladores](../extensibility/specifying-file-handlers-for-file-name-extensions.md) de archivos para extensiones de nombre de archivo Proporciona información sobre cómo registrar las aplicaciones que pueden abrir, editar, etc., una extensión de nombre de archivo determinada.

- [Registrar verbos para extensiones](../extensibility/registering-verbs-for-file-name-extensions.md) de nombre de archivo Describe cómo registrar verbos.

- [Administrar asociaciones de archivos en paralelo](../extensibility/managing-side-by-side-file-associations.md) Describe cómo controlar las instalaciones en paralelo en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] las que se debe invocar una versión determinada de para abrir un archivo.

## <a name="related-sections"></a>Secciones relacionadas
- [Admite varias versiones de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md) Describe problemas relacionados con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] varias versiones de VSPackage durante el desarrollo y la implementación para los usuarios finales.
