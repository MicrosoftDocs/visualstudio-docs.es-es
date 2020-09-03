---
title: Registro de extensiones de nombre de archivo para implementaciones en paralelo | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701548"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>Registrar las extensiones de nombre de archivo para implementaciones en paralelo
En el caso de los VSPackages implementados en un entorno en paralelo, debe registrar las extensiones de nombre de archivo para asociar los archivos con la versión correcta de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . A menos que use una extensión de nombre de archivo específica de la versión, el registro permite a los usuarios abrir los archivos de proyecto y de elemento de proyecto en la versión adecuada de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="in-this-section"></a>En esta sección
- [Acerca de las extensiones de nombre de archivo](../extensibility/about-file-name-extensions.md) Describe cómo se registran las extensiones de nombre de archivo.

- [Especificar controladores de archivos para las extensiones de nombre de archivo](../extensibility/specifying-file-handlers-for-file-name-extensions.md) Proporciona información sobre cómo registrar las aplicaciones que pueden abrir, editar, etc., una extensión de nombre de archivo determinada.

- [Registrar verbos para las extensiones de nombre de archivo](../extensibility/registering-verbs-for-file-name-extensions.md) Describe cómo registrar verbos.

- [Administrar asociaciones de archivos en paralelo](../extensibility/managing-side-by-side-file-associations.md) Describe cómo controlar instalaciones en paralelo en las que se debe invocar una versión determinada de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para abrir un archivo.

## <a name="related-sections"></a>Secciones relacionadas
- [Compatibilidad con varias versiones de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md) Describe los problemas relacionados con varias versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y su VSPackage durante el desarrollo y la implementación para los usuarios finales.
