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
ms.openlocfilehash: 03948506d928f7d638b21c1fa4bc0a35818ec09a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545428"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116: Los métodos APTCA deben llamar solo a métodos APTCA

|||
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|Identificador de comprobación|CA2116|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo

Un método en un ensamblado con el <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> atributo llama a un método en un ensamblado que no tiene el atributo.

## <a name="rule-description"></a>Descripción de la regla

De forma predeterminada, los métodos públicos o protegidos en ensamblados con nombres seguros implícitamente están protegidos por un [peticiones de vínculo](/dotnet/framework/misc/link-demands) de plena confianza; sólo de plena confianza para los autores de llamadas pueden tener acceso a un ensamblado con nombre seguro. Los ensamblados con nombre seguro marcados con el <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo (APTCA) no tiene esta protección. El atributo deshabilita la petición de vínculo, lo que el ensamblado puede tener acceso a los llamadores que no tienen plena confianza, como el código que se ejecuta desde una intranet o Internet.

Cuando el atributo APTCA está presente en un ensamblado de plena confianza y el ensamblado ejecuta código en otro ensamblado que no permite a llamadores parcialmente confiables, es posible un ataque de seguridad. Si dos métodos `M1` y `M2` cumplen las condiciones siguientes, los llamadores malintencionados pueden usar el método `M1` para omitir la petición de vínculo de plena confianza implícita que protege `M2`:

- `M1` ¿se declara un método público en un ensamblado de plena confianza que tiene el atributo APTCA.

- `M1` llama a un método `M2` fuera `M1`del ensamblado.

- `M2`del ensamblado no tiene el atributo APTCA y, por lo tanto, no debe ejecutarse por o en nombre de los llamadores de confianza parcial.

Un llamador de confianza parcial `X` puede llamar al método `M1`, haciendo que `M1` para llamar a `M2`. Dado que `M2` no tiene el atributo APTCA, su llamador inmediato (`M1`) debe satisfacer una petición de vínculo de plena confianza; `M1` es de plena confianza y, por tanto, supera esta comprobación. El riesgo de seguridad es porque `X` no participa en el cumplimiento de la petición de vínculo que protege `M2` es de confianza. Por lo tanto, los métodos con el atributo APTCA no deben llamar a métodos que no tienen el atributo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Si el atributo APCTA es necesario, use una petición para proteger el método que llama en el ensamblado de plena confianza. Los permisos exactos demanda dependerá de la funcionalidad expuesta por el método. Si es posible, proteja el método con una petición de plena confianza para asegurarse de que la funcionalidad subyacente no se expone a llamadores de confianza parcial. Si esto no es posible, seleccione un conjunto de permisos que protege eficazmente la funcionalidad expuesta.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Para suprimir una advertencia de esta regla de forma segura, debe asegurarse de que la funcionalidad expuesta por el método no directa o indirectamente permiten que los llamadores tener acceso a información confidencial, operaciones o los recursos que se pueden usar de forma destructiva.

## <a name="example-1"></a>Ejemplo 1
 El ejemplo siguiente utiliza dos ensamblados y una aplicación de prueba para ilustrar que esta regla detecta la vulnerabilidad de seguridad. El primer ensamblado no tiene el atributo APTCA y no debe estar accesible a los llamadores de confianza parcial (representado por `M2` en la explicación anterior).

 [!code-csharp[FxCop.Security.NoAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_1.cs)]

## <a name="example-2"></a>Ejemplo 2
 El segundo ensamblado es de plena confianza y permite llamadores parcialmente confiables (representado por `M1` en la explicación anterior).

 [!code-csharp[FxCop.Security.YesAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_2.cs)]

## <a name="example-3"></a>Ejemplo 3
 La aplicación de prueba (representado por `X` en la explicación anterior) es de confianza parcial.

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_3.cs)]

Este ejemplo produce el siguiente resultado:

```txt
Demand for full trust:Request failed.
ClassRequiringFullTrust.DoWork was called.
```

## <a name="related-rules"></a>Reglas relacionadas

- [CA2117: Los tipos APTCA solo amplían tipos base APTCA](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>Vea también

- [Instrucciones de codificación segura](/dotnet/standard/security/secure-coding-guidelines)
- [Utilizar bibliotecas de código que no es de plena confianza](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)
- [Peticiones de vínculo](/dotnet/framework/misc/link-demands)
- [Datos y modelado](/dotnet/framework/data/index)