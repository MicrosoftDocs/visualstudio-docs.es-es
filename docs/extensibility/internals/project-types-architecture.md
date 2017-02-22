---
title: "Arquitectura de los tipos de proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "proyectos [Visual Studio SDK], arquitectura"
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# Arquitectura de los tipos de proyecto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Esta sección contiene información detallada sobre la arquitectura de tipos de proyecto de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## En esta sección  
 [Elementos de un modelo de proyecto](../../extensibility/internals/elements-of-a-project-model.md)  
 Muestra los servicios que un tipo de proyecto puede utilizar y las interfaces debe implementar.  
  
 [Componentes principales de modelo de proyecto](../../extensibility/internals/project-model-core-components.md)  
 Describe los tipos de proyecto de las interfaces que ambos deben implementar y que pueden implementar opcionalmente para proporcionar funcionalidad adicional.  
  
 [Cuándo crear tipos de proyecto](../../extensibility/internals/when-to-create-project-types.md)  
 Le ayuda a decidir cuándo debe crear un tipo de proyecto y cuándo se puede utilizar otra característica de extensibilidad de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] como VSPackages y editores para lograr el mismo objetivo.  
  
 [Selección y jerarquías](../../extensibility/internals/hierarchies-and-selection.md)  
 Describe cómo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utiliza jerarquías y contexto de selección para proporcionar una experiencia coherente y simplificada del usuario.  
  
## Secciones relacionadas  
 [Subtipos de proyecto](../../extensibility/internals/project-subtypes.md)  
 Explica cómo los subtipos de proyecto permiten personalizar el comportamiento de los sistemas de proyectos de [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] y de[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].  
  
 [Tipos de proyecto](../../extensibility/internals/project-types.md)  
 Proporciona información general sobre proyectos como bloques de creación básicos del entorno de desarrollo integrado de \(IDE\) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Los vínculos se proporcionan a los otros temas que explican cómo código que compila y de compilación del control de proyectos.