---
title: "CA2116: Los m&#233;todos APTCA deben llamar solo a m&#233;todos APTCA | Microsoft Docs"
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
  - "AptcaMethodsShouldOnlyCallAptcaMethods"
  - "CA2116"
helpviewer_keywords: 
  - "AptcaMethodsShouldOnlyCallAptcaMethods"
  - "CA2116"
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2116: Los m&#233;todos APTCA deben llamar solo a m&#233;todos APTCA
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|  
|Identificador de comprobación|CA2116|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un método de un ensamblado con el atributo <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> llama a un método de un ensamblado que no tiene el atributo.  
  
## Descripción de la regla  
 De forma predeterminada, los métodos públicos o protegidos de los ensamblados con nombres seguros quedan protegidos de forma implícita mediante [Link Demands](../Topic/Link%20Demands.md) de plena confianza; sólo los llamadores de plena confianza pueden obtener acceso a un ensamblado con nombre seguro.  Los ensamblados con nombre seguro marcados con el atributo <xref:System.Security.AllowPartiallyTrustedCallersAttribute> \(APTCA\) no tienen esta protección.  El atributo deshabilita una solicitud de vínculo haciendo que los llamadores que no tienen plena confianza puedan obtener acceso al ensamblado, como la ejecución de código desde una intranet o Internet.  
  
 Si está presente el atributo APTCA en un ensamblado con plena confianza y el ensamblado ejecuta código en otro ensamblado que permite llamadores parcialmente confiables, se puede producir un ataque en el sistema de seguridad.  Si dos métodos `M1` y `M2` cumplen las condiciones siguientes, los llamadores malintencionados pueden hacer que el método `M1` omita la solicitud implícita de vínculo de plena confianza que protege `M2`:  
  
-   `M1` es un método público declarado en un ensamblado de plena confianza que tiene el atributo APTCA.  
  
-   `M1` llama a un método `M2` fuera del ensamblado de `M1`.  
  
-   El ensamblado de `M2` no tiene el atributo APTCA y, por consiguiente, no debería ejecutarse por los llamadores que no son de plena confianza ni en su nombre.  
  
 Un llamador `X` que no es de plena confianza puede llamar al método `M1`, provocando que `M1` llame a `M2`.  Puesto que `M2` no tiene el atributo APTCA, el llamador inmediato \(`M1`\) debe cumplir la solicitud de vínculo de plena confianza; `M1` es de plena confianza y, por tanto, supera esta comprobación.  El riesgo de seguridad es porque `X` no participa en el cumplimiento de la solicitud de vínculo que protege `M2` que no es de confianza.  Por lo tanto, los métodos con el atributo APTCA no deben llamar a métodos que no tengan el atributo.  
  
## Cómo corregir infracciones  
 Si el atributo APCTA es necesario, use una petición para proteger el método que llama en el ensamblado de plena confianza.  Los permisos exactos que se solicitan dependerán de la funcionalidad expuesta por el método.  Si es posible, proteja el método con una solicitud de plena confianza para asegurarse de que la funcionalidad subyacente no se expone a llamadores que no son de plena confianza.  Si esto no es posible, seleccione un conjunto de permisos que proteja eficazmente la funcionalidad expuesta.  Para obtener más información acerca de las peticiones, vea [Demands](http://msdn.microsoft.com/es-es/e5283e28-2366-4519-b27d-ef5c1ddc1f48).  
  
## Cuándo suprimir advertencias  
 Para suprimir una advertencia de esta regla de forma segura, debe asegurase de que la funcionalidad expuesta por el método no permite directa ni indirectamente que los llamadores tengan acceso a información confidencial, operaciones o recursos que se puedan usar de forma destructiva.  
  
## Ejemplo  
 El ejemplo siguiente utiliza dos ensamblados y una aplicación de prueba para mostrar la vulnerabilidad de seguridad detectada por esta regla.  El primer ensamblado no tiene el atributo APTCA y los llamadores que no son de plena confianza no deberían tener acceso a él \(representado por `M2` en la explicación anterior\).  
  
 [!code-cs[FxCop.Security.NoAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_1.cs)]  
  
## Ejemplo  
 El segundo ensamblado es de plena confianza y permite el acceso de llamadores que no son de plena confianza \(representado por `M1` en la explicación anterior\).  
  
 [!code-cs[FxCop.Security.YesAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_2.cs)]  
  
## Ejemplo  
 La aplicación de prueba \(representada por `X` en la explicación anterior\) no es de plena confianza.  
  
 [!code-cs[FxCop.Security.TestAptcaMethods#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_3.cs)]  
  
 Este ejemplo produce el siguiente resultado:  
  
  **Solicitud de plena confianza: se produjo un error en la solicitud.**  
**Se llamó a ClassRequiringFullTrust.DoWork.**   
## Reglas relacionadas  
 [CA2117: Los tipos APTCA solo amplían tipos base APTCA](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)  
  
## Vea también  
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [.NET Framework Assemblies Callable by Partially Trusted Code](http://msdn.microsoft.com/es-es/a417fcd4-d3ca-4884-a308-3a1a080eac8d)   
 [Using Libraries from Partially Trusted Code](../Topic/Using%20Libraries%20from%20Partially%20Trusted%20Code.md)   
 [Demands](http://msdn.microsoft.com/es-es/e5283e28-2366-4519-b27d-ef5c1ddc1f48)   
 [Link Demands](../Topic/Link%20Demands.md)   
 [Datos y modelado](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)