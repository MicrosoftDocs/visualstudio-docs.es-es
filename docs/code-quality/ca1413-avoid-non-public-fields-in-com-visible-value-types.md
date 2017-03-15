---
title: "CA1413: Evite campos no p&#250;blicos en tipos de valor visibles para COM | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1413"
  - "AvoidNonpublicFieldsInComVisibleValueTypes"
helpviewer_keywords: 
  - "CA1413"
  - "AvoidNonpublicFieldsInComVisibleValueTypes"
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1413: Evite campos no p&#250;blicos en tipos de valor visibles para COM
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|  
|Identificador de comprobación|CA1413|  
|Categoría|Microsoft.Interoperability|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo de valor marcado específicamente como visible para el Modelo de objetos componentes \(COM\) declara un campo de instancia no público.  
  
## Descripción de la regla  
 Los campos de instancia no públicos de tipos de valor visibles para COM están visibles para los clientes COM.  Revise el contenido del campo para obtener información que no deba exponerse o que tendrá un impacto no deseado sobre la seguridad o el diseño.  
  
 De forma predeterminada, todos los tipos de valor públicos están visibles para COM.  Sin embargo, esta regla exige que se indique la visibilidad COM del tipo explícitamente para reducir los falsos positivos.  El ensamblado contenedor se debe marcar con el <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> establecido en `false` y el tipo se debe marcar con el <xref:System.Runtime.InteropServices.ComVisibleAttribute> establecido en `true`.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla y mantener el campo oculto, cambie el tipo de valor a un tipo de referencia o quite el atributo <xref:System.Runtime.InteropServices.ComVisibleAttribute> del tipo.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si es aceptable que este campo se exponga públicamente.  
  
## Ejemplo  
 El siguiente ejemplo muestra un tipo que infringe la regla.  
  
 [!code-cs[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/CSharp/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.cs)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/VisualBasic/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.vb)]  
  
## Reglas relacionadas  
 [CA1407: Evite miembros estáticos en tipos visibles para COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)  
  
 [CA1017: Marcar los ensamblados con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## Vea también  
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Qualifying .NET Types for Interoperation](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)