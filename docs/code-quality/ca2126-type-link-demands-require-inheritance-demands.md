---
title: 'CA2126: Las peticiones de vínculos de tipos requieren peticiones de herencias'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
helpviewer_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
ms.assetid: 07b604e5-5579-4df9-a578-dadd0d8370a7
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2be42519f87c3c040c1f80c80d53d490853d986e
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920762"
---
# <a name="ca2126-type-link-demands-require-inheritance-demands"></a>CA2126: Las peticiones de vínculos de tipos requieren peticiones de herencias

|||
|-|-|
|TypeName|TypeLinkDemandsRequireInheritanceDemands|
|Identificador de comprobación|CA2126|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
Un tipo público no sellado está protegido con una petición de vínculo, tiene un método reemplazable y ni el tipo ni el método están protegidos con una petición de herencia.

## <a name="rule-description"></a>Descripción de la regla
Una petición de vínculo en un método o su tipo declarativo requiere que el llamador inmediato del método tenga el permiso especificado. Una petición de herencia en un método requiere un método de reemplazo para tener el permiso especificado. Una petición de herencia en un tipo requiere una clase derivada para tener el permiso especificado.

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
[CA2108: Revisar la seguridad declarativa en los tipos de valor](../code-quality/ca2108-review-declarative-security-on-value-types.md)

[CA2112: Los tipos seguros no deberían exponer campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

[CA2122: No exponer indirectamente métodos con peticiones de vínculo](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)

[CA2123: La invalidación de las peticiones de vínculo debe ser idéntica a la base](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)

## <a name="see-also"></a>Vea también

- [Instrucciones de codificación segura](/dotnet/standard/security/secure-coding-guidelines)
- [Peticiones de vínculo](/dotnet/framework/misc/link-demands)