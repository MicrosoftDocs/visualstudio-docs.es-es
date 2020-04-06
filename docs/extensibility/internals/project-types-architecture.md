---
title: Arquitectura de tipos de proyecto (Project Types Architecture) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e53929b1ec2ed9c73191bf16f1cedc84a53b58f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706320"
---
# <a name="project-types-architecture"></a>Arquitectura de tipos de proyecto
Esta sección contiene información detallada sobre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]la arquitectura de los tipos de proyecto en .

## <a name="in-this-section"></a>En esta sección
- [Elementos de un modelo de proyecto](../../extensibility/internals/elements-of-a-project-model.md)

 Enumera los servicios que puede consumir un tipo de proyecto y las interfaces que debe implementar.

- [Componentes principales del modelo de proyecto](../../extensibility/internals/project-model-core-components.md)

 Describe los tipos de proyecto de interfaces deben implementarse y, opcionalmente, pueden implementarse para proporcionar funcionalidad adicional.

- [Momento para la creación de tipos de proyecto](../../extensibility/internals/when-to-create-project-types.md)

 Le ayuda a decidir cuándo debe crear un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tipo de proyecto y cuándo puede usar otra característica de extensibilidad como VSPackages y editores para lograr el mismo objetivo.

- [Jerarquías y selección](../../extensibility/internals/hierarchies-and-selection.md)

 Describe cómo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se usan las jerarquías y el contexto de selección para proporcionar una experiencia de usuario coherente y simplificada.

## <a name="related-sections"></a>Secciones relacionadas
- [Subtipos de proyecto](../../extensibility/internals/project-subtypes.md)

 Explica cómo los subtipos de proyecto permiten [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] personalizar [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]el comportamiento de los sistemas de proyecto de y .

- [Tipos de proyecto](../../extensibility/internals/project-types.md)

 Proporciona una visión general de los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proyectos como los bloques básicos del entorno de desarrollo integrado (IDE). Se proporcionan vínculos a temas adicionales que explican cómo los proyectos controlan la creación y compilación de código.
