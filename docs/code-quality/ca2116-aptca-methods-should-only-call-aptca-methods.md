---
title: 'CA2116: Los métodos APTCA deben llamar solo a métodos APTCA'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 70affcf0b71e9d0ae7440141f45f5ae0f2c04bf6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
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
 De forma predeterminada, los métodos públicos o protegidos de ensamblados con nombres seguros implícitamente están protegidos por un [peticiones de vínculo](/dotnet/framework/misc/link-demands) de plena confianza; solo de plena confianza para los autores de llamada pueden tener acceso a un ensamblado con nombre seguro. Los ensamblados con nombre seguro marcados con el <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo (APTCA) no tiene esta protección. El atributo deshabilita la petición de vínculo, lo que el ensamblado puede tener acceso a los llamadores que no tienen plena confianza, por ejemplo, el código que se ejecuta desde una intranet o Internet.

 Si el atributo APTCA está presente en un ensamblado de plena confianza y el ensamblado ejecuta código en otro ensamblado que no permite a llamadores parcialmente confiables, es posible un ataque de seguridad. Si dos métodos `M1` y `M2` cumplen las condiciones siguientes, los llamadores malintencionados pueden usar el método `M1` para omitir la petición de vínculo de plena confianza implícita que protege `M2`:

-   `M1` es un método público que se declara en un ensamblado de plena confianza que tiene el atributo APTCA.

-   `M1` llama a un método `M2` fuera `M1`del ensamblado.

-   `M2`del ensamblado no tiene el atributo APTCA y, por lo tanto, no debe ejecutarse por o en nombre de los llamadores de confianza parcial.

 Un llamador de confianza parcial `X` puede llamar al método `M1`, con lo que `M1` para llamar a `M2`. Dado que `M2` no tiene el atributo APTCA, su llamador inmediato (`M1`) debe satisfacer una petición de vínculo de plena confianza; `M1` es de plena confianza y, por tanto, supera esta comprobación. El riesgo de seguridad es porque `X` no participa en el cumplimiento de la petición de vínculo que protege `M2` de llamadores de confianza. Por lo tanto, los métodos con el atributo APTCA no deben llamar métodos que no tienen el atributo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Si el atributo APCTA es necesario, use una petición para proteger el método que llama al ensamblado de plena confianza. Los permisos exactos que se solicitan dependerán de la funcionalidad expuesta por el método. Si es posible, proteja el método con una petición de plena confianza para asegurarse de que la funcionalidad subyacente no se expone a los llamadores de confianza parcial. Si esto no es posible, seleccione un conjunto de permisos que proteja eficazmente la funcionalidad expuesta.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Para suprimir una advertencia de esta regla de forma segura, debe asegurarse de que la funcionalidad expuesta por el método no directa ni indirectamente que los llamadores tener acceso a información confidencial, operaciones o recursos que se pueden usar de forma destructiva.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente utiliza dos ensamblados y una aplicación de prueba para ilustrar la vulnerabilidad de seguridad detectada por esta regla. El primer ensamblado no tiene el atributo APTCA y no debe estar accesible a los llamadores de confianza parcial (representado por `M2` en la explicación anterior).

 [!code-csharp[FxCop.Security.NoAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_1.cs)]

## <a name="example"></a>Ejemplo
 El segundo ensamblado es de plena confianza y permite llamadores parcialmente confiables (representado por `M1` en la explicación anterior).

 [!code-csharp[FxCop.Security.YesAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_2.cs)]

## <a name="example"></a>Ejemplo
 La aplicación de prueba (representada por `X` en la explicación anterior) es de confianza parcial.

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_3.cs)]

 Este ejemplo produce el siguiente resultado:

 **Solicitar código de plena confianza: error en la solicitud. ** 
 **ClassRequiringFullTrust.DoWork se llamó.**
## <a name="related-rules"></a>Reglas relacionadas
 [CA2117: Los tipos APTCA solo amplían tipos base APTCA](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>Vea también
 [Instrucciones de codificación segura](/dotnet/standard/security/secure-coding-guidelines) [utilizar parcialmente bibliotecas de código de confianza](/dotnet/framework/misc/using-libraries-from-partially-trusted-code) [las peticiones de vínculo](/dotnet/framework/misc/link-demands) [datos y modelado](/dotnet/framework/data/index)