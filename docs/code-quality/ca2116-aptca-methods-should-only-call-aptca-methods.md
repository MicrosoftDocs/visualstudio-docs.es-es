---
title: 'CA2116: Los métodos APTCA deben llamar solo a métodos APTCA'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f55c48583e47a4602f33d69799d1d86a6c9c3e56
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921156"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116: Los métodos APTCA deben llamar solo a métodos APTCA

|||
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|Identificador de comprobación|CA2116|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa

Un método de un ensamblado con <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> el atributo llama a un método de un ensamblado que no tiene el atributo.

## <a name="rule-description"></a>Descripción de la regla

De forma predeterminada, los métodos públicos o protegidos en ensamblados con nombres seguros están protegidos implícitamente por una [solicitud de vínculo](/dotnet/framework/misc/link-demands) de plena confianza; solo los llamadores de plena confianza pueden tener acceso a un ensamblado con nombre seguro. Los ensamblados con nombre seguro marcados con el <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo (APTCA) no tienen esta protección. El atributo deshabilita la petición de vínculo, lo que hace que el ensamblado sea accesible a los llamadores que no tienen plena confianza, como el código que se ejecuta desde una intranet o Internet.

Cuando el atributo APTCA está presente en un ensamblado de plena confianza y el ensamblado ejecuta código en otro ensamblado que no permite llamadores parcialmente confiables, es posible que se produzca un ataque de seguridad. Si dos métodos `M1` y `M2` cumplen las condiciones siguientes, los llamadores malintencionados pueden usar `M1` el método para omitir la petición de vínculo de `M2`plena confianza implícita que protege:

- `M1`es un método público declarado en un ensamblado de plena confianza que tiene el atributo APTCA.

- `M1`llama a un `M2` método `M1`fuera del ensamblado de.

- `M2`el ensamblado de no tiene el atributo APTCA y, por lo tanto, no debe ser ejecutado por ni en nombre de llamadores que sean de confianza parcial.

Un llamador `X` de confianza parcial puede llamar `M1`al método `M1` , lo `M2`que hace que llame a. Dado `M2` que no tiene el atributo APTCA, su llamador inmediato (`M1`) debe satisfacer una petición de vínculo para plena confianza; `M1` tiene plena confianza y, por tanto, satisface esta comprobación. El riesgo de seguridad se `X` debe a que no participa en satisfacer la petición de `M2` vínculo que protege de los llamadores que no son de confianza. Por lo tanto, los métodos con el atributo APTCA no deben llamar a métodos que no tienen el atributo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Si se requiere el atributo APCTA, use una solicitud para proteger el método que llama al ensamblado de plena confianza. Los permisos exactos que exija dependerán de la funcionalidad expuesta por el método. Si es posible, proteja el método con una demanda de plena confianza para asegurarse de que la funcionalidad subyacente no se expone a los llamadores de confianza parcial. Si esto no es posible, seleccione un conjunto de permisos que proteja de forma eficaz la funcionalidad expuesta.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Para suprimir de forma segura una advertencia de esta regla, debe asegurarse de que la funcionalidad expuesta por el método no permita directa o indirectamente a los autores de llamadas acceder a información confidencial, operaciones o recursos que se puedan usar de manera destructiva.

## <a name="example-1"></a>Ejemplo 1
En el ejemplo siguiente se usan dos ensamblados y una aplicación de prueba para ilustrar la vulnerabilidad de seguridad detectada por esta regla. El primer ensamblado no tiene el atributo APTCA y no debe ser accesible para llamadores de confianza parcial (representado `M2` por en la explicación anterior).

[!code-csharp[FxCop.Security.NoAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_1.cs)]

## <a name="example-2"></a>Ejemplo 2
El segundo ensamblado es de plena confianza y permite llamadores parcialmente confiables `M1` (representados por en la explicación anterior).

[!code-csharp[FxCop.Security.YesAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_2.cs)]

## <a name="example-3"></a>Ejemplo 3
La aplicación de prueba (representada por `X` en la explicación anterior) es de confianza parcial.

[!code-csharp[FxCop.Security.TestAptcaMethods#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_3.cs)]

Este ejemplo produce el siguiente resultado:

```txt
Demand for full trust:Request failed.
ClassRequiringFullTrust.DoWork was called.
```

## <a name="related-rules"></a>Reglas relacionadas

- [CA2117: Los tipos APTCA solo deben extender los tipos base APTCA](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>Vea también

- [Instrucciones de codificación segura](/dotnet/standard/security/secure-coding-guidelines)
- [Utilizar bibliotecas de código que no es de plena confianza](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)
- [Peticiones de vínculo](/dotnet/framework/misc/link-demands)
- [Datos y modelado](/dotnet/framework/data/index)