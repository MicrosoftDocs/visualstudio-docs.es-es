---
title: "CA2126: Las peticiones de v&#237;nculos de tipos requieren peticiones de herencias | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2126"
  - "TypeLinkDemandsRequireInheritanceDemands"
helpviewer_keywords: 
  - "CA2126"
  - "TypeLinkDemandsRequireInheritanceDemands"
ms.assetid: 07b604e5-5579-4df9-a578-dadd0d8370a7
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2126: Las peticiones de v&#237;nculos de tipos requieren peticiones de herencias
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypeLinkDemandsRequireInheritanceDemands|  
|Identificador de comprobación|CA2126|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo público no sellado está protegido con una petición de vínculo, tiene un método reemplazable y ni el tipo ni el método están protegidos con una petición de herencia.  
  
## Descripción de la regla  
 Una petición de vínculo en un método o su tipo declarativo exige que el llamador inmediato del método tenga el permiso especificado.  Una petición de herencia en un método exige que un método reemplazante tenga el permiso especificado.  Una petición de herencia en un tipo exige que una clase derivada tenga el permiso especificado.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, proteja el tipo o el método con una petición de herencia para el mismo permiso que la petición de vínculo.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 El siguiente ejemplo muestra un tipo que infringe la regla.  
  
 [!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CPP/ca2126-type-link-demands-require-inheritance-demands_1.cpp)]
 [!code-vb[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/VisualBasic/ca2126-type-link-demands-require-inheritance-demands_1.vb)]
 [!code-cs[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2126-type-link-demands-require-inheritance-demands_1.cs)]  
  
## Reglas relacionadas  
 [CA2108: Revisar la seguridad declarativa en los tipos de valor](../code-quality/ca2108-review-declarative-security-on-value-types.md)  
  
 [CA2112: Los tipos seguros no deberían exponer campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
 [CA2122: No exponer indirectamente métodos con peticiones de vínculos](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)  
  
 [CA2123: Las peticiones de vínculos de reemplazo deberían ser idénticas a la base](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)  
  
## Vea también  
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [Inheritance Demands](http://msdn.microsoft.com/es-es/28b9adbb-8f08-4f10-b856-dbf59eb932d9)   
 [Link Demands](../Topic/Link%20Demands.md)   
 [Demands](http://msdn.microsoft.com/es-es/e5283e28-2366-4519-b27d-ef5c1ddc1f48)