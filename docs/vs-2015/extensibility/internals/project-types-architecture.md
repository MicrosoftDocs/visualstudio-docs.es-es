---
title: Arquitectura de los tipos de proyecto | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 775656d2190a36f62c2b047c1ff7f1e02575c1ca
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58989336"
---
# <a name="project-types-architecture"></a>Arquitectura de tipos de proyecto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Esta sección contiene información detallada sobre la arquitectura de tipos de proyecto en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="in-this-section"></a>En esta sección  
 [Elementos de un modelo de proyecto](../../extensibility/internals/elements-of-a-project-model.md)  
 Enumera los servicios que puede consumir un tipo de proyecto y las interfaces que debe implementar.  
  
 [Componentes principales del modelo de proyecto](../../extensibility/internals/project-model-core-components.md)  
 Describe las interfaces, tipos de proyecto, deben implementar tanto si lo desea, pueden implementar para proporcionar funcionalidad adicional.  
  
 [Momento para la creación de tipos de proyecto](../../extensibility/internals/when-to-create-project-types.md)  
 Escriba ayuda a decidir cuándo debe crear un proyecto y cuándo se puede utilizar otro [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] característica de extensibilidad, como los paquetes VSPackage y editores para lograr el mismo objetivo.  
  
 [Jerarquías y selección](../../extensibility/internals/hierarchies-and-selection.md)  
 Describe cómo [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] jerarquías y el contexto de selección se utiliza para proporcionar una experiencia de usuario coherente y simplificada.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Subtipos de proyecto](../../extensibility/internals/project-subtypes.md)  
 Explica cómo los subtipos de proyecto le permiten personalizar el comportamiento de los sistemas del proyecto de [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] y [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)].  
  
 [Tipos de proyecto](../../extensibility/internals/project-types.md)  
 Proporciona información general de los proyectos como bloques de creación básicos de la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] el entorno de desarrollo integrado (IDE). Se proporcionan vínculos a temas adicionales que explican cómo proyectos de control de generar y compilar código.
