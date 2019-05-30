---
title: Arquitectura de los tipos de proyecto | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d77524097509c45c23d6a3d9cc147e5aba6691d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318897"
---
# <a name="project-types-architecture"></a>Arquitectura de tipos de proyecto
Esta sección contiene información detallada sobre la arquitectura de tipos de proyecto en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="in-this-section"></a>En esta sección
- [Elementos de un modelo de proyecto](../../extensibility/internals/elements-of-a-project-model.md)

 Enumera los servicios que puede consumir un tipo de proyecto y las interfaces que debe implementar.

- [Componentes principales del modelo de proyecto](../../extensibility/internals/project-model-core-components.md)

 Describe las interfaces, tipos de proyecto, deben implementar tanto si lo desea, pueden implementar para proporcionar funcionalidad adicional.

- [Momento para la creación de tipos de proyecto](../../extensibility/internals/when-to-create-project-types.md)

 Escriba ayuda a decidir cuándo debe crear un proyecto y cuándo se puede utilizar otro [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] característica de extensibilidad, como los paquetes VSPackage y editores para lograr el mismo objetivo.

- [Jerarquías y selección](../../extensibility/internals/hierarchies-and-selection.md)

 Describe cómo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jerarquías y el contexto de selección se utiliza para proporcionar una experiencia de usuario coherente y simplificada.

## <a name="related-sections"></a>Secciones relacionadas
- [Subtipos de proyecto](../../extensibility/internals/project-subtypes.md)

 Explica cómo los subtipos de proyecto le permiten personalizar el comportamiento de los sistemas del proyecto de [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] y [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].

- [Tipos de proyecto](../../extensibility/internals/project-types.md)

 Proporciona información general de los proyectos como bloques de creación básicos de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE). Se proporcionan vínculos a temas adicionales que explican cómo proyectos de control de generar y compilar código.