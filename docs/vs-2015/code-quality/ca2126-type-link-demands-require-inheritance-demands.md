---
title: 'CA2126: Peticiones de vínculos de tipos requieren peticiones de herencias | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
helpviewer_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
ms.assetid: 07b604e5-5579-4df9-a578-dadd0d8370a7
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2fbf1a5f49e86cdc672f7b79207753d4d1949cf7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58995777"
---
# <a name="ca2126-type-link-demands-require-inheritance-demands"></a>CA2126: Las peticiones de vínculos de tipos requieren peticiones de herencias
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypeLinkDemandsRequireInheritanceDemands|
|Identificador de comprobación|CA2126|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo público no sellado está protegido con una petición de vínculo, tiene un método reemplazable y ni el tipo ni el método está protegido con una petición de herencia.

## <a name="rule-description"></a>Descripción de la regla
 Una petición de vínculo en un método o su tipo declarativo requiere que el llamador inmediato del método tenga el permiso especificado. Una petición de herencia en un método requiere un método de reemplazo tenga el permiso especificado. Una petición de herencia en un tipo requiere una clase derivada para tener el permiso especificado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, proteja el tipo o el método con una petición de herencia para el mismo permiso como la petición de vínculo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo que infringe la regla.

 [!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.TypesWithLinkDemands/cpp/FxCop.Security.TypesWithLinkDemands.cpp#1)]
 [!code-csharp[FxCop.Security.TypesWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypesWithLinkDemands/cs/FxCop.Security.TypesWithLinkDemands.cs#1)]
 [!code-vb[FxCop.Security.TypesWithLinkDemands#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.TypesWithLinkDemands/vb/FxCop.Security.TypesWithLinkDemands.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2108: Revisar la seguridad declarativa en los tipos de valor](../code-quality/ca2108-review-declarative-security-on-value-types.md)

 [CA2112: Los tipos seguros no deberían exponer campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA2122: No exponer indirectamente métodos con peticiones de vínculo](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)

 [CA2123: Las peticiones de vínculo deben ser idénticas de base](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)

## <a name="see-also"></a>Vea también
 [Instrucciones de codificación segura](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [peticiones de herencias](http://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) [peticiones de vínculos](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [demandas](http://msdn.microsoft.com/e5283e28-2366-4519-b27d-ef5c1ddc1f48)
