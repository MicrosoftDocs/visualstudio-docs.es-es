---
title: 'CA2117: los tipos APTCA solo deben extender los tipos base APTCA | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 90c1f66f36fc689ee077ec66f154487d65ee13a1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543616"
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117: Los tipos APTCA solo amplían tipos base APTCA
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|
|Identificador de comprobación|CA2117|
|Category|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un tipo público o protegido de un ensamblado con el <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> atributo hereda de un tipo declarado en un ensamblado que no tiene el atributo.

## <a name="rule-description"></a>Descripción de la regla
 De forma predeterminada, los tipos públicos o protegidos en ensamblados con nombres seguros están protegidos implícitamente por una [solicitud de herencia](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) de plena confianza. Los ensamblados con nombre seguro marcados con el <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo (APTCA) no tienen esta protección. El atributo deshabilita la petición de herencia. Esto hace que los tipos expuestos declarados en el ensamblado sean heredables por tipos que no tienen plena confianza.

 Cuando el atributo APTCA está presente en un ensamblado de plena confianza y un tipo del ensamblado se hereda de un tipo que no permite llamadores parcialmente confiables, es posible que se produzca un ataque de seguridad. Si dos tipos `T1` y `T2` cumplen las condiciones siguientes, los llamadores malintencionados pueden usar el tipo `T1` para omitir la demanda implícita de herencia de plena confianza que protege `T2` :

- `T1` es un tipo público declarado en un ensamblado de plena confianza que tiene el atributo APTCA.

- `T1` hereda de un tipo `T2` fuera de su ensamblado.

- `T2`el ensamblado de no tiene el atributo APTCA y, por tanto, no debe ser heredable por los tipos de ensamblados de confianza parcial.

  Un tipo de confianza parcial `X` puede heredar de `T1` , que le da acceso a los miembros heredados declarados en `T2` . Dado `T2` que no tiene el atributo APTCA, su tipo derivado inmediato ( `T1` ) debe satisfacer una petición de herencia de plena confianza; `T1` tiene plena confianza y, por tanto, satisface esta comprobación. El riesgo de seguridad se debe `X` a que no participa en el cumplimiento de la demanda de herencia que protege de la subclase que no es `T2` de confianza. Por esta razón, los tipos con el atributo APTCA no deben extender los tipos que no tienen el atributo.

  Otro problema de seguridad, y quizás uno más común, es que el tipo derivado ( `T1` ) puede, a través de un error del programador, exponer miembros protegidos del tipo que requiere plena confianza ( `T2` ). Cuando esto ocurre, los llamadores que no son de confianza obtienen acceso a la información que solo debe estar disponible para los tipos de plena confianza.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Si el tipo indicado por la infracción está en un ensamblado que no requiere el atributo APTCA, quítelo.

 Si se requiere el atributo APTCA, agregue una solicitud de herencia para la plena confianza al tipo. Esto protege contra la herencia por tipos que no son de confianza.

 Es posible corregir una infracción agregando el atributo APTCA a los ensamblados de los tipos base informados por la infracción. No lo haga sin realizar primero una revisión de seguridad intensiva de todo el código de los ensamblados y todo el código que dependa de los ensamblados.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Para suprimir de forma segura una advertencia de esta regla, debe asegurarse de que los miembros protegidos expuestos por su tipo no permitan directa o indirectamente a los llamadores que no son de confianza acceder a información confidencial, operaciones o recursos que se pueden usar de forma destructiva.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se usan dos ensamblados y una aplicación de prueba para ilustrar la vulnerabilidad de seguridad detectada por esta regla. El primer ensamblado no tiene el atributo APTCA y no debe ser heredable por tipos de confianza parcial (representado por `T2` en la explicación anterior).

 [!code-csharp[FxCop.Security.NoAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptcaInherit/cs/FxCop.Security.NoAptcaInherit.cs#1)]

## <a name="example"></a>Ejemplo
 El segundo ensamblado, representado por `T1` en la explicación anterior, es de plena confianza y permite llamadores de confianza parcial.

 [!code-csharp[FxCop.Security.YesAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptcaInherit/cs/FxCop.Security.YesAptcaInherit.cs#1)]

## <a name="example"></a>Ejemplo
 El tipo de prueba, representado por `X` en la explicación anterior, está en un ensamblado de confianza parcial.

 [!code-csharp[FxCop.Security.TestAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaInherit/cs/FxCop.Security.TestAptcaInherit.cs#1)]

 Este ejemplo produce el siguiente resultado:

 **Reúnase en el glen 2/22/2003 12:00:00 AM!** 
 **De prueba: praderas** 
 soleadas **Reúnase en el Prado soleado 2/22/2003 12:00:00 AM.**
## <a name="related-rules"></a>Reglas relacionadas
 [CA2116: Los métodos APTCA deben llamar solo a métodos APTCA](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)

## <a name="see-also"></a>Consulte también
 [Instrucciones de codificación segura](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [.NET Framework ensamblados a los que puede llamar el código de confianza parcial](https://msdn.microsoft.com/a417fcd4-d3ca-4884-a308-3a1a080eac8d) [mediante bibliotecas de peticiones de herencia de código de confianza parcial](https://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74) [Inheritance Demands](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9)
