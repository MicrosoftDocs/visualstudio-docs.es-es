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
ms.openlocfilehash: 832d2c9fc1d4b9138a7cd1bc39868b3c4bf1b814
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232642"
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117: Los tipos APTCA solo amplían tipos base APTCA

|||
|-|-|
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|
|Identificador de comprobación|CA2117|
|Categoría|Microsoft.Security|
|Cambio importante|Problemático|

## <a name="cause"></a>Motivo

Un tipo público o protegido de un ensamblado con <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> el atributo hereda de un tipo declarado en un ensamblado que no tiene el atributo.

## <a name="rule-description"></a>Descripción de la regla

De forma predeterminada, los tipos públicos o protegidos en ensamblados con nombres seguros están protegidos implícitamente por un [InheritanceDemand](xref:System.Security.Permissions.SecurityAction#System_Security_Permissions_SecurityAction_InheritanceDemand) para plena confianza. Los ensamblados con nombre seguro marcados con el <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo (APTCA) no tienen esta protección. El atributo deshabilita la petición de herencia. Los tipos expuestos declarados en un ensamblado sin una petición de herencia son heredables por tipos que no tienen plena confianza.

Cuando el atributo APTCA está presente en un ensamblado de plena confianza y un tipo del ensamblado se hereda de un tipo que no permite llamadores parcialmente confiables, es posible que se produzca un ataque de seguridad. Si dos tipos `T1` y `T2` cumplen las condiciones siguientes, los llamadores malintencionados pueden usar `T1` el tipo para omitir la demanda implícita de herencia `T2`de plena confianza que protege:

- `T1`es un tipo público declarado en un ensamblado de plena confianza que tiene el atributo APTCA.

- `T1`hereda de un tipo `T2` fuera de su ensamblado.

- `T2`el ensamblado de no tiene el atributo APTCA y, por tanto, no debe ser heredable por los tipos de ensamblados de confianza parcial.

Un tipo `X` de confianza parcial puede heredar de `T1`, que le da acceso a los miembros `T2`heredados declarados en. Dado `T2` que no tiene el atributo APTCA, su tipo derivado inmediato (`T1`) debe satisfacer una petición de herencia de plena confianza; `T1` tiene plena confianza y, por tanto, satisface esta comprobación. El riesgo de seguridad se `X` debe a que no participa en el cumplimiento de la `T2` demanda de herencia que protege de la subclase que no es de confianza. Por esta razón, los tipos con el atributo APTCA no deben extender los tipos que no tienen el atributo.

Otro problema de seguridad, y quizás uno más común, es que el tipo derivado (`T1`) puede, a través de un error del programador, exponer miembros protegidos del tipo que requiere`T2`plena confianza (). Cuando se produce esta exposición, los llamadores que no son de confianza obtienen acceso a la información que solo debe estar disponible para los tipos de plena confianza.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Si el tipo indicado por la infracción está en un ensamblado que no requiere el atributo APTCA, quítelo.

Si se requiere el atributo APTCA, agregue una solicitud de herencia para la plena confianza al tipo. La petición de herencia protege contra la herencia por tipos que no son de confianza.

Es posible corregir una infracción agregando el atributo APTCA a los ensamblados de los tipos base informados por la infracción. No lo haga sin realizar primero una revisión de seguridad intensiva de todo el código de los ensamblados y todo el código que dependa de los ensamblados.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Para suprimir de forma segura una advertencia de esta regla, debe asegurarse de que los miembros protegidos expuestos por su tipo no permitan directa o indirectamente a los llamadores que no son de confianza acceder a información confidencial, operaciones o recursos que se pueden usar de forma destructiva.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se usan dos ensamblados y una aplicación de prueba para ilustrar la vulnerabilidad de seguridad detectada por esta regla. El primer ensamblado no tiene el atributo APTCA y no debe ser heredable por tipos de confianza parcial (representado `T2` por en la explicación anterior).

[!code-csharp[FxCop.Security.NoAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_1.cs)]

El segundo ensamblado, representado `T1` por en la explicación anterior, es de plena confianza y permite llamadores de confianza parcial.

[!code-csharp[FxCop.Security.YesAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_2.cs)]

El tipo de prueba, representado `X` por en la explicación anterior, está en un ensamblado de confianza parcial.

[!code-csharp[FxCop.Security.TestAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_3.cs)]

Este ejemplo produce el siguiente resultado:

```txt
Meet at the shady glen 2/22/2003 12:00:00 AM!
From Test: sunny meadow
Meet at the sunny meadow 2/22/2003 12:00:00 AM!
```

## <a name="related-rules"></a>Reglas relacionadas

[CA2116 Los métodos APTCA solo deben llamar a métodos APTCA](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)

## <a name="see-also"></a>Vea también

- [Instrucciones de codificación segura](/dotnet/standard/security/secure-coding-guidelines)
- [Utilizar bibliotecas de código que no es de plena confianza](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)
