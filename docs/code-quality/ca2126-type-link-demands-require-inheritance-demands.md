---
title: "CA2126: Las peticiones de vínculos de tipos requieren peticiones de herencias | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
helpviewer_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
ms.assetid: 07b604e5-5579-4df9-a578-dadd0d8370a7
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 254fd15f97afe69f927bb8a1aae1954105776641
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca2126-type-link-demands-require-inheritance-demands"></a>CA2126: Las peticiones de vínculos de tipos requieren peticiones de herencias
|||  
|-|-|  
|TypeName|TypeLinkDemandsRequireInheritanceDemands|  
|Identificador de comprobación|CA2126|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un tipo público no sellado está protegido con una petición de vínculo, tiene un método reemplazable y ni el tipo ni el método está protegido con una petición de herencia.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Una petición de vínculo en un método o su tipo declarativo requiere que el llamador inmediato del método tenga el permiso especificado. Una petición de herencia en un método requiere un método de reemplazo tenga el permiso especificado. Una petición de herencia en un tipo requiere una clase derivada tenga el permiso especificado.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, proteja el tipo o el método con una petición de herencia para el mismo permiso que la petición de vínculo.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un tipo que infringe la regla.  
  
 [!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CPP/ca2126-type-link-demands-require-inheritance-demands_1.cpp)]
 [!code-vb[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/VisualBasic/ca2126-type-link-demands-require-inheritance-demands_1.vb)]
 [!code-csharp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2126-type-link-demands-require-inheritance-demands_1.cs)]  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA2108: Revisar la seguridad declarativa en los tipos de valores](../code-quality/ca2108-review-declarative-security-on-value-types.md)  
  
 [CA2112: Los tipos seguros no deberían exponer campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
 [CA2122: No exponer indirectamente métodos con peticiones de vínculos](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)  
  
 [CA2123: Las peticiones de vínculo de invalidaciones deberían ser idénticas a la base](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)  
  
## <a name="see-also"></a>Vea también  
 [Instrucciones de codificación segura](/dotnet/standard/security/secure-coding-guidelines)   
 [Peticiones de herencia](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9)   
 [Peticiones de vínculo](/dotnet/framework/misc/link-demands)   
 [Peticiones](http://msdn.microsoft.com/en-us/e5283e28-2366-4519-b27d-ef5c1ddc1f48)