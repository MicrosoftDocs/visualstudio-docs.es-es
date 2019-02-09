---
title: 'CA2117: Los tipos APTCA solo amplían tipos base APTCA'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 43b294d72c8f8ec317803f2aa400e9cc50693162
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55935425"
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117: Los tipos APTCA solo amplían tipos base APTCA

|||
|-|-|
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|
|Identificador de comprobación|CA2117|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo

Un tipo público o protegido en un ensamblado con el <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> atributo hereda de un tipo declarado en un ensamblado que no tiene el atributo.

## <a name="rule-description"></a>Descripción de la regla

De forma predeterminada, los tipos públicos o protegidos en ensamblados con nombres seguros implícitamente están protegidos por un [InheritanceDemand](xref:System.Security.Permissions.SecurityAction#System_Security_Permissions_SecurityAction_InheritanceDemand) de plena confianza. Los ensamblados con nombre seguro marcados con el <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo (APTCA) no tiene esta protección. El atributo deshabilita la petición de herencia. Los tipos expuestos declarados en un ensamblado sin una petición de herencia pueden heredarlos tipos que no tienen plena confianza.

Cuando el atributo APTCA está presente en un ensamblado de plena confianza y un tipo en el ensamblado se hereda de un tipo que no permite a llamadores parcialmente confiables, es posible un ataque de seguridad. Si dos tipos `T1` y `T2` cumplen las condiciones siguientes, los llamadores malintencionados pueden usar el tipo `T1` para omitir la petición de herencia de plena confianza implícita que protege `T2`:

- `T1` ¿se declara un tipo público en un ensamblado de plena confianza que tiene el atributo APTCA.

- `T1` hereda de un tipo `T2` fuera del ensamblado.

- `T2`del ensamblado no tiene el atributo APTCA y, por lo tanto, no debe ser heredable por tipos en ensamblados de confianza parcial.

Un tipo de confianza parcial `X` puede heredar de `T1`, que le concede acceso a los miembros heredados que se declaran en `T2`. Dado que `T2` no tiene el atributo APTCA, su tipo derivado inmediato (`T1`) debe satisfacer una petición de herencia de plena confianza; `T1` es de plena confianza y, por tanto, supera esta comprobación. El riesgo de seguridad es porque `X` no participa en el cumplimiento de la petición de herencia que protege `T2` de creación de subclases de confianza. Por este motivo, los tipos con el atributo APTCA no deben ampliar tipos que no tienen el atributo.

Otro problema de seguridad y quizás uno más comunes, que es el tipo derivado (`T1`) puede, a través de los errores de programador, exponer miembros protegidos desde el tipo que requiere plena confianza (`T2`). Cuando se produce esta exposición, los llamadores de confianza acceder a información que debe estar disponible solo para los tipos de plena confianza.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Si el tipo de la infracción ha informado de un ensamblado que no requiere el atributo APTCA, elimínelo.

Si el atributo APTCA es necesario, agregue una petición de herencia de plena confianza para el tipo. La petición de herencia se protege contra la herencia de tipos de confianza.

Es posible corregir una infracción agregando el atributo APTCA a los ensamblados de los tipos base notificados por la infracción. No lo hace sin la primera, llevar a cabo una revisión de seguridad con uso intensivo de todo el código en los ensamblados y todo el código que depende de los ensamblados.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Para suprimir una advertencia de esta regla de forma segura, debe asegurarse de que los miembros protegidos expuestos por el tipo no directa o indirectamente que los llamadores de confianza tener acceso a información confidencial, operaciones o los recursos que se pueden usar de forma destructiva.

## <a name="example"></a>Ejemplo

El ejemplo siguiente utiliza dos ensamblados y una aplicación de prueba para ilustrar que esta regla detecta la vulnerabilidad de seguridad. El primer ensamblado no tiene el atributo APTCA y debe no ser puede heredarse mediante tipos de confianza parcial (representado por `T2` en la explicación anterior).

[!code-csharp[FxCop.Security.NoAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_1.cs)]

El segundo ensamblado, representado por `T1` en la sección anterior, es de plena confianza y permite llamadores parcialmente confiables.

[!code-csharp[FxCop.Security.YesAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_2.cs)]

El tipo de prueba, representado por `X` en la sección anterior, se encuentra en un ensamblado de confianza parcial.

[!code-csharp[FxCop.Security.TestAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_3.cs)]

Este ejemplo produce el siguiente resultado:

```txt
Meet at the shady glen 2/22/2003 12:00:00 AM!
From Test: sunny meadow
Meet at the sunny meadow 2/22/2003 12:00:00 AM!
```

## <a name="related-rules"></a>Reglas relacionadas

[CA2116: LOS métodos APTCA solo deben llamar a métodos APTCA](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)

## <a name="see-also"></a>Vea también

- [Instrucciones de codificación segura](/dotnet/standard/security/secure-coding-guidelines)
- [Utilizar bibliotecas de código que no es de plena confianza](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)
