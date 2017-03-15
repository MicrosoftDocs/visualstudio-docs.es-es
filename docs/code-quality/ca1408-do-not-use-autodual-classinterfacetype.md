---
title: "CA1408: No utilizar AutoDual ClassInterfaceType | Microsoft Docs"
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
  - "DoNotUseAutoDualClassInterfaceType"
  - "CA1408"
helpviewer_keywords: 
  - "CA1408"
  - "DoNotUseAutoDualClassInterfaceType"
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1408: No utilizar AutoDual ClassInterfaceType
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseAutoDualClassInterfaceType|  
|Identificador de comprobación|CA1408|  
|Categoría|Microsoft.Interoperability|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo visible para el Modelo de objetos componentes \(COM\) está marcado con el atributo <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> establecido en el valor `AutoDual` de <xref:System.Runtime.InteropServices.ClassInterfaceType>.  
  
## Descripción de la regla  
 Los tipos que utilizan una interfaz dual permiten a los clientes enlazarse a un diseño de interfaz concreto.  Cualquier cambio que se introduzca en una versión futura en el diseño del tipo o en cualquier tipo base provocará un error en los clientes COM que están enlazados a la interfaz.  De forma predeterminada, si no se especifica el atributo <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>, se utiliza una interfaz sólo de envío.  
  
 A menos que se marque lo contrario, todos los tipos públicos no genéricos son visibles para COM; todos los tipos no públicos y genéricos son invisibles para COM.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el valor del atributo <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> al valor `None` de <xref:System.Runtime.InteropServices.ClassInterfaceType> y defina la interfaz de manera explícita.  
  
## Cuándo suprimir advertencias  
 No suprima ninguna advertencia de esta regla a no ser que esté absolutamente seguro de que el diseño del tipo y sus tipos base no van a cambiar en una versión posterior.  
  
## Ejemplo  
 El ejemplo siguiente muestra una clase que infringe la regla y una nueva declaración de la clase de modo que utilice una interfaz explícita.  
  
 [!code-cs[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]  
  
## Reglas relacionadas  
 [CA1403: Los tipos de diseño automático no deben ser visibles para COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)  
  
 [CA1412: Marcar las interfaces ComSource como IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)  
  
## Vea también  
 [Introducing the Class Interface](http://msdn.microsoft.com/es-es/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [Qualifying .NET Types for Interoperation](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)