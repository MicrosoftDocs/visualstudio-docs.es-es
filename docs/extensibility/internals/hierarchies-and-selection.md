---
title: Jerarquías y selección | Microsoft Docs
description: Obtenga información sobre cómo Visual Studio controla las jerarquías, como los proyectos, y cómo utiliza el contexto de selección para determinar lo que se muestra al usuario.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, hierarchies
- selection
- hierarchies
ms.assetid: cad0a859-7a84-4ce5-b0a9-f7f64e5f8ebb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 04f433e3da45e10d2b1721ac13254856489d2d0a
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480426"
---
# <a name="hierarchies-and-selection"></a>Jerarquías y selección
Al personalizar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , debe entender cómo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] controla las jerarquías, como los proyectos, y cómo utiliza el contexto de selección para determinar lo que se muestra al usuario. En esta sección se describen los conceptos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jerarquías y selección.

## <a name="in-this-section"></a>En esta sección
- [Jerarquías en Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)

 Describe las jerarquías de proyecto y el concepto general de jerarquías.

- [Selección y moneda en el IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)

 Describe cómo el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno de desarrollo integrado (IDE) mantiene información acerca de los objetos actualmente activos del usuario y permite que VSPackages realice el seguimiento de la moneda.

- [Objetos de contexto de selección](../../extensibility/internals/selection-context-objects.md)

 Describe el modelo de cómo puede determinar el foco del contexto de selección del usuario en una ventana.

- [Comentarios al usuario](../../extensibility/internals/feedback-to-the-user.md)

 Describe cómo la funcionalidad disponible en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se basa en el contexto de selección actual del usuario y en el contexto global del IDE.

## <a name="related-sections"></a>Secciones relacionadas
- [Arquitectura de tipos de proyecto](../../extensibility/internals/project-types-architecture.md)

 Proporciona información técnica detallada acerca de los tipos de proyecto.
