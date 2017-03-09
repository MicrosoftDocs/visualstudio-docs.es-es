---
title: "CA2117: Los tipos APTCA solo ampl&#237;an tipos base APTCA | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2117"
  - "AptcaTypesShouldOnlyExtendAptcaBaseTypes"
helpviewer_keywords: 
  - "AptcaTypesShouldOnlyExtendAptcaBaseTypes"
  - "CA2117"
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2117: Los tipos APTCA solo ampl&#237;an tipos base APTCA
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|  
|Identificador de comprobación|CA2117|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo público o protegido en un ensamblado con el atributo <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> hereda de un tipo declarado en un ensamblado que no tiene el atributo.  
  
## Descripción de la regla  
 De forma predeterminada, [Inheritance Demands](http://msdn.microsoft.com/es-es/28b9adbb-8f08-4f10-b856-dbf59eb932d9) protege implícitamente los tipos públicos o protegidos de ensamblados con nombres seguros y de plena confianza.  Los ensamblados con nombre seguro marcados con el atributo <xref:System.Security.AllowPartiallyTrustedCallersAttribute> \(APTCA\) no tienen esta protección.  El atributo deshabilita la solicitud de herencia.  Esto hace que los tipos expuestos declarados en el ensamblado los puedan heredar tipos que no son de plena confianza.  
  
 Si está presente el atributo APTCA en un ensamblado con plena confianza y un tipo del ensamblado se hereda de otro que permite llamadores parcialmente confiables, se puede producir un ataque en el sistema de seguridad.  Si dos tipos `T1` y `T2` cumplen las condiciones siguientes, los llamadores malintencionados pueden hacer que el tipo `T1` omita la solicitud implícita de vínculo de plena confianza que protege `T2`:  
  
-   `T1` es un tipo público declarado en un ensamblado de plena confianza que tiene el atributo APTCA.  
  
-   `T1` hereda de un tipo `T2` fuera de su ensamblado.  
  
-   El ensamblado de `T2` no tiene el atributo APTCA y, por consiguiente, no lo deben heredar los tipos en ensamblados que no son de plena confianza.  
  
 Un tipo `X` de confianza parcial puede heredar de `T1`, que le da acceso a los miembros heredados declarados en `T2`.  Puesto que `T2` no tiene el atributo APTCA, su tipo derivado inmediato \(`T1`\) debe cumplir una solicitud de herencia de plena confianza; `T1` es de plena confianza y, por tanto, supera esta comprobación.  Existe un riesgo de seguridad porque `X` no participa en el cumplimiento de la solicitud de herencia que protege `T2` de subclases que no son de plena confianza.  Por esta razón, los tipos con el atributo APTCA no deben extender los que no lo tengan.  
  
 Otro problema de seguridad, y quizás uno más habitual, es que el tipo derivado \(`T1`\) puede, por un error del programador, exponer miembros protegidos desde el tipo que requiere plena confianza \(`T2`\).  En este caso, los llamadores que no son de plena confianza obtienen acceso a la información que sólo debería estar disponible para los de plena confianza.  
  
## Cómo corregir infracciones  
 Si el tipo del que la infracción ha informado está en un ensamblado que no requiere el atributo APTCA, quítelo.  
  
 Si se requiere el atributo APTCA, agregue una solicitud de herencia de plena confianza para el tipo.  De esta forma, los tipos que no son de confianza se protegen contra la herencia.  
  
 Es posible corregir una infracción agregando el atributo APTCA a los ensamblados de los tipos base de los que informó la infracción.  No lleve a cabo esta acción sin revisar primero y a fondo la seguridad de todo el código de los ensamblados, así como todo el código que depende de ellos.  
  
## Cuándo suprimir advertencias  
 Para suprimir una advertencia de esta regla de forma segura, se debe asegura de que los miembros protegidos expuestos por el tipo no permiten, directa ni indirectamente, que los llamadores que no sean de confianza tengan acceso a información confidencial, operaciones ni recursos que se puedan usar de forma destructiva.  
  
## Ejemplo  
 El ejemplo siguiente utiliza dos ensamblados y una aplicación de prueba para mostrar la vulnerabilidad de seguridad detectada por esta regla.  El primer ensamblado no tiene el atributo APTCA y los tipos de confianza parcial lo heredan \(representados por `T2` en la descripción anterior\).  
  
 [!code-cs[FxCop.Security.NoAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_1.cs)]  
  
## Ejemplo  
 El segundo ensamblado, representado por `T1` en la descripción previa, es de plena confianza y permite llamadores de confianza parcial.  
  
 [!code-cs[FxCop.Security.YesAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_2.cs)]  
  
## Ejemplo  
 El tipo de prueba, representado por `X` en la descripción anterior, está en un ensamblado de confianza parcial.  
  
 [!code-cs[FxCop.Security.TestAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_3.cs)]  
  
 Este ejemplo produce el siguiente resultado:  
  
  **¡Quedar en la cañada sombría el 22\/2\/2003 a las 12:00:00 a.m.\!**  
**De la prueba: prado soleado**  
**¡Quedar en el prado soleado el 22\/2\/2003 a las 12:00:00 a.m.\!**   
## Reglas relacionadas  
 [CA2116: Los métodos APTCA deben llamar solo a métodos APTCA](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)  
  
## Vea también  
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [.NET Framework Assemblies Callable by Partially Trusted Code](http://msdn.microsoft.com/es-es/a417fcd4-d3ca-4884-a308-3a1a080eac8d)   
 [Using Libraries from Partially Trusted Code](../Topic/Using%20Libraries%20from%20Partially%20Trusted%20Code.md)   
 [Inheritance Demands](http://msdn.microsoft.com/es-es/28b9adbb-8f08-4f10-b856-dbf59eb932d9)