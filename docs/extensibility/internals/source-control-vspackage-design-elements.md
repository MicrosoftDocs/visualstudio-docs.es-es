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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 24a9b8dfa8036603c035a9112eb29688eab7ff25
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852614"
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
