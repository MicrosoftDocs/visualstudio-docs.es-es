---
title: 'CA2116: Los métodos APTCA solo deben llamar a métodos APTCA | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c9de5178b585275ef410ad3179ba320b663536bf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658678"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116: Los métodos APTCA deben llamar solo a métodos APTCA
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|Identificador de comprobación|CA2116|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método de un ensamblado con el atributo <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> llama a un método de un ensamblado que no tiene el atributo.

## <a name="rule-description"></a>Descripción de la regla
 De forma predeterminada, los métodos públicos o protegidos en ensamblados con nombres seguros están protegidos implícitamente por una [solicitud de vínculo](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) de plena confianza; solo los llamadores de plena confianza pueden tener acceso a un ensamblado con nombre seguro. Los ensamblados con nombre seguro marcados con el atributo <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) no tienen esta protección. El atributo deshabilita la petición de vínculo, lo que hace que el ensamblado sea accesible a los llamadores que no tienen plena confianza, como el código que se ejecuta desde una intranet o Internet.

 Cuando el atributo APTCA está presente en un ensamblado de plena confianza y el ensamblado ejecuta código en otro ensamblado que no permite llamadores parcialmente confiables, es posible que se produzca un ataque de seguridad. Si dos métodos `M1` y `M2` cumplen las condiciones siguientes, los llamadores malintencionados pueden usar el método `M1` para omitir la petición de vínculo de plena confianza implícita que protege `M2`:

- `M1` es un método público declarado en un ensamblado de plena confianza que tiene el atributo APTCA.

- `M1` llama a un método `M2` fuera del ensamblado de `M1`.

- el ensamblado de `M2` no tiene el atributo APTCA y, por lo tanto, no debe ser ejecutado por ni en nombre de llamadores que sean de confianza parcial.

  Un llamador de confianza parcial `X` puede llamar al método `M1`, lo que hace que `M1` llame a `M2`. Dado que `M2` no tiene el atributo APTCA, su llamador inmediato (`M1`) debe satisfacer una petición de vínculo para plena confianza;  `M1` tiene plena confianza y, por tanto, satisface esta comprobación. El riesgo de seguridad se debe a que `X` no participa en satisfacer la petición de vínculo que protege `M2` de los llamadores que no son de confianza. Por lo tanto, los métodos con el atributo APTCA no deben llamar a métodos que no tienen el atributo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Si se requiere el atributo APCTA, use una solicitud para proteger el método que llama al ensamblado de plena confianza. Los permisos exactos que exija dependerán de la funcionalidad expuesta por el método. Si es posible, proteja el método con una demanda de plena confianza para asegurarse de que la funcionalidad subyacente no se expone a los llamadores de confianza parcial. Si esto no es posible, seleccione un conjunto de permisos que proteja de forma eficaz la funcionalidad expuesta. Para obtener más información sobre las peticiones, consulte [demands](https://msdn.microsoft.com/e5283e28-2366-4519-b27d-ef5c1ddc1f48).

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Para suprimir de forma segura una advertencia de esta regla, debe asegurarse de que la funcionalidad expuesta por el método no permita directa o indirectamente a los autores de llamadas acceder a información confidencial, operaciones o recursos que se puedan usar de manera destructiva.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se usan dos ensamblados y una aplicación de prueba para ilustrar la vulnerabilidad de seguridad detectada por esta regla. El primer ensamblado no tiene el atributo APTCA y no debe ser accesible para llamadores de confianza parcial (representado por `M2` en la explicación anterior).

 [!code-csharp[FxCop.Security.NoAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptca/cs/FxCop.Security.NoAptca.cs#1)]

## <a name="example"></a>Ejemplo
 El segundo ensamblado es de plena confianza y permite llamadores parcialmente confiables (representados por `M1` en la explicación anterior).

 [!code-csharp[FxCop.Security.YesAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptca/cs/FxCop.Security.YesAptca.cs#1)]

## <a name="example"></a>Ejemplo
 La aplicación de prueba (representada por `X` en la explicación anterior) es de confianza parcial.

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaMethods/cs/FxCop.Security.TestAptcaMethods.cs#1)]

 Este ejemplo produce el siguiente resultado:

 **Demanda de plena confianza: error en la solicitud.** 
**ClassRequiringFullTrust. el trabajo se llamó.**
## <a name="related-rules"></a>Reglas relacionadas
 [CA2117: Los tipos APTCA solo deben extender los tipos base APTCA ](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>Vea también
 [Instrucciones de codificación segura](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [.NET Framework ensamblados a los que puede llamar el código de confianza parcial](https://msdn.microsoft.com/a417fcd4-d3ca-4884-a308-3a1a080eac8d) [mediante bibliotecas de solicitudes de código de confianza parcial](https://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74) [Solicitudes ](https://msdn.microsoft.com/e5283e28-2366-4519-b27d-ef5c1ddc1f48) [Solicitudes de vínculos](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [Datos y modelado](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
