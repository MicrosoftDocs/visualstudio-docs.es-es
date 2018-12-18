---
title: 'CA2117: Los tipos APTCA solo amplían tipos base APTCA | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4b069674827ab266b4a4b7a99f81e039d487f6da
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49922658"
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117: Los tipos APTCA solo amplían tipos base APTCA
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|
|Identificador de comprobación|CA2117|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo público o protegido en un ensamblado con el <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> atributo hereda de un tipo declarado en un ensamblado que no tiene el atributo.

## <a name="rule-description"></a>Descripción de la regla
 De forma predeterminada, los tipos públicos o protegidos en ensamblados con nombres seguros implícitamente están protegidos por un [peticiones de herencias](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9) de plena confianza. Los ensamblados con nombre seguro marcados con el <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo (APTCA) no tiene esta protección. El atributo deshabilita la petición de herencia. Esto hace que sea declarados en el ensamblado heredables tipos expuestos por los tipos que no tienen plena confianza.

 Cuando el atributo APTCA está presente en un ensamblado de plena confianza y un tipo en el ensamblado se hereda de un tipo que no permite a llamadores parcialmente confiables, es posible un ataque de seguridad. Si dos tipos `T1` y `T2` cumplen las condiciones siguientes, los llamadores malintencionados pueden usar el tipo `T1` para omitir la petición de herencia de plena confianza implícita que protege `T2`:

- `T1` ¿se declara un tipo público en un ensamblado de plena confianza que tiene el atributo APTCA.

- `T1` hereda de un tipo `T2` fuera del ensamblado.

- `T2`del ensamblado no tiene el atributo APTCA y, por lo tanto, no debe ser heredable por tipos en ensamblados de confianza parcial.

  Un tipo de confianza parcial `X` puede heredar de `T1`, que le concede acceso a los miembros heredados que se declaran en `T2`. Dado que `T2` no tiene el atributo APTCA, su tipo derivado inmediato (`T1`) debe satisfacer una petición de herencia de plena confianza; `T1` es de plena confianza y, por tanto, supera esta comprobación. El riesgo de seguridad es porque `X` no participa en el cumplimiento de la petición de herencia que protege `T2` de creación de subclases de confianza. Por este motivo, los tipos con el atributo APTCA no deben ampliar tipos que no tienen el atributo.

  Otro problema de seguridad y quizás uno más comunes, que es el tipo derivado (`T1`) puede, a través de los errores de programador, exponer miembros protegidos desde el tipo que requiere plena confianza (`T2`). Cuando esto sucede, los llamadores de confianza acceder a información que debe estar disponible solo para los tipos de plena confianza.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Si el tipo de la infracción ha informado de un ensamblado que no requiere el atributo APTCA, elimínelo.

 Si el atributo APTCA es necesario, agregue una petición de herencia de plena confianza para el tipo. Esto protege contra la herencia de tipos de confianza.

 Es posible corregir una infracción agregando el atributo APTCA a los ensamblados de los tipos base notificados por la infracción. No lo hace sin la primera, llevar a cabo una revisión de seguridad con uso intensivo de todo el código en los ensamblados y todo el código que depende de los ensamblados.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Para suprimir una advertencia de esta regla de forma segura, debe asegurarse de que los miembros protegidos expuestos por el tipo no directa o indirectamente que los llamadores de confianza tener acceso a información confidencial, operaciones o los recursos que se pueden usar de forma destructiva.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente utiliza dos ensamblados y una aplicación de prueba para ilustrar que esta regla detecta la vulnerabilidad de seguridad. El primer ensamblado no tiene el atributo APTCA y debe no ser puede heredarse mediante tipos de confianza parcial (representado por `T2` en la explicación anterior).

 [!code-csharp[FxCop.Security.NoAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptcaInherit/cs/FxCop.Security.NoAptcaInherit.cs#1)]

## <a name="example"></a>Ejemplo
 El segundo ensamblado, representado por `T1` en la sección anterior, es de plena confianza y permite llamadores parcialmente confiables.

 [!code-csharp[FxCop.Security.YesAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptcaInherit/cs/FxCop.Security.YesAptcaInherit.cs#1)]

## <a name="example"></a>Ejemplo
 El tipo de prueba, representado por `X` en la sección anterior, se encuentra en un ensamblado de confianza parcial.

 [!code-csharp[FxCop.Security.TestAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaInherit/cs/FxCop.Security.TestAptcaInherit.cs#1)]

 Este ejemplo produce el siguiente resultado:

 **Cumplir en el glen turbio 2/22/2003 12:00:00 A.M.! ** 
 **De prueba: soleado meadow**
**cumple en el soleado meadow 2/22/2003 12:00:00 A.M.!**
## <a name="related-rules"></a>Reglas relacionadas
 [CA2116: Los métodos APTCA deben llamar solo a métodos APTCA](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)

## <a name="see-also"></a>Vea también
 [Instrucciones de codificación segura](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [ensamblados de .NET Framework invocables por código de confianza parcial](http://msdn.microsoft.com/en-us/a417fcd4-d3ca-4884-a308-3a1a080eac8d) [utilizar parcialmente bibliotecas de código de confianza](http://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74) [peticiones de herencias](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9)




