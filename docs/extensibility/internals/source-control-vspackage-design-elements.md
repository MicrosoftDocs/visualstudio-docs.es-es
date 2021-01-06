---
title: Elementos de diseño del VSPackage de control de código fuente | Microsoft Docs
description: Obtenga información sobre la estructura que debe implementar el VSPackage de control de código fuente y las interfaces y servicios que el VSPackage de control de código fuente puede implementar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e586470208989dce070c92963fc215f1053559a4
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877655"
---
# <a name="source-control-vspackage-design-elements"></a>Elementos de diseño de VSPackage de control de código fuente
En los temas de esta sección se describe la estructura que debe implementar el VSPackage de control de código fuente para la integración profunda. También se enumeran las interfaces y servicios que el VSPackage de control de código fuente puede implementar y las interfaces y servicios que el VSPackage de control de código fuente puede usar desde otros [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] componentes para admitir su modelo de control de código fuente y su funcionalidad.

## <a name="in-this-section"></a>En esta sección
- [Estructura de VSPackage](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)

 Define la estructura del VSPackage de control de código fuente.

- [Interfaces y servicios relacionados](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

 Enumera las interfaces y servicios relacionados con los paquetes de control de código fuente.

- [Servicios proporcionados](../../extensibility/internals/services-provided-source-control-vspackage.md)

 Describe el servicio de control de código fuente proporcionado por el VSPackage de control de código fuente.

## <a name="related-sections"></a>Secciones relacionadas
- [Creación de un VSPackage de control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Describe cómo crear un VSPackage de control de código fuente que no solo proporciona la funcionalidad de control de código fuente, sino que se puede usar para personalizar la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaz de usuario del control de código fuente.
