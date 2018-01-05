---
title: "CA2117: Los tipos APTCA solo amplían tipos base APTCA | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: be208c156e8710b6aa6b2821a5a85131f3c2e4b2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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
 De forma predeterminada, públicos o protegidos en ensamblados con nombres seguros protege implícitamente los tipos por un <xref:System.Security.Permissions.SecurityAction.InheritanceDemand> de plena confianza. Los ensamblados con nombre seguro marcados con el <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo (APTCA) no tiene esta protección. El atributo deshabilita la petición de herencia. Por ello, declarados en el ensamblado heredables tipos expuestos por los tipos que no tienen plena confianza.  
  
 Si el atributo APTCA está presente en un ensamblado de plena confianza y un tipo en el ensamblado se hereda de un tipo que no permite a llamadores parcialmente confiables, es posible un ataque de seguridad. Si dos tipos `T1` y `T2` cumplen las condiciones siguientes, los llamadores malintencionados pueden usar el tipo `T1` para omitir la petición de herencia de plena confianza implícita que protege `T2`:  
  
-   `T1`¿se declara un tipo público en un ensamblado de plena confianza que tiene el atributo APTCA.  
  
-   `T1`hereda de un tipo `T2` fuera del ensamblado.  
  
-   `T2`del ensamblado no tiene el atributo APTCA y, por lo tanto, no debe ser heredable por tipos en ensamblados de confianza parcial.  
  
 Un tipo de confianza parcial `X` puede heredar de `T1`, que le da acceso a los miembros heredados declarados en `T2`. Dado que `T2` no tiene el atributo APTCA, su tipo derivado inmediato (`T1`) debe satisfacer una petición de herencia de plena confianza; `T1` es de plena confianza y, por tanto, supera esta comprobación. El riesgo de seguridad es porque `X` no participa en el cumplimiento de la petición de herencia que protege `T2` desde subclases no es de confianza. Por este motivo, los tipos con el atributo APTCA no deben extenderse tipos que no tienen el atributo.  
  
 Otro problema de seguridad y quizás uno más habitual, que es el tipo derivado (`T1`) puede, a través de error del programador, exponer miembros protegidos desde el tipo que requiere plena confianza (`T2`). Cuando esto ocurre, los llamadores de confianza tener acceso a información que debe estar disponible solo para los tipos de plena confianza.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Si el tipo de la infracción ha informado está en un ensamblado que no requiere el atributo APTCA, quítelo.  
  
 Si se requiere el atributo APTCA, agregue una petición de herencia de plena confianza para el tipo. Esto protege contra la herencia de tipos de confianza.  
  
 Es posible corregir una infracción agregando el atributo APTCA a los ensamblados de los tipos base notificados por la infracción. De no hacerlo sin primera llevar a cabo una revisión de seguridad de uso intensivo de todo el código en los ensamblados y todo el código que depende de los ensamblados.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Para suprimir una advertencia de esta regla de forma segura, debe asegurarse de que los miembros protegidos expuestos por el tipo no directa o indirectamente que los llamadores tengan acceso a información confidencial, operaciones o recursos que se pueden usar de forma destructiva.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente utiliza dos ensamblados y una aplicación de prueba para ilustrar la vulnerabilidad de seguridad detectada por esta regla. El primer ensamblado no tiene el atributo APTCA y no debe ser pueden heredar tipos de confianza parcial (representado por `T2` en la explicación anterior).  
  
 [!code-csharp[FxCop.Security.NoAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_1.cs)]  
  
## <a name="example"></a>Ejemplo  
 El segundo ensamblado, representado por `T1` en la descripción anterior, es de plena confianza y permite llamadores parcialmente confiables.  
  
 [!code-csharp[FxCop.Security.YesAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_2.cs)]  
  
## <a name="example"></a>Ejemplo  
 El tipo de prueba, representado por `X` en la descripción anterior, está en un ensamblado de confianza parcial.  
  
 [!code-csharp[FxCop.Security.TestAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_3.cs)]  
  
 Este ejemplo produce el siguiente resultado:  
  
 **Cumple en el poco glen 22/2/2003 12:00:00 AM.**  
**De prueba: Sol praderas**  
**Cumple en el sol praderas 22/2/2003 12:00:00 AM.**   
## <a name="related-rules"></a>Reglas relacionadas  
 [CA2116: Los métodos APTCA deben llamar solo a métodos APTCA](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)  
  
## <a name="see-also"></a>Vea también  
 [Instrucciones de codificación segura](/dotnet/standard/security/secure-coding-guidelines)   
 [Utilizar bibliotecas de código de confianza parcial](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)   
