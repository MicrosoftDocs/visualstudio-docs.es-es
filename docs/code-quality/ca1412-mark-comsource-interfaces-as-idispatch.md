---
title: "CA1412: Marcar las interfaces ComSource como IDispatch | Microsoft Docs"
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
  - "MarkComSourceInterfacesAsIDispatch"
  - "CA1412"
helpviewer_keywords: 
  - "CA1412"
  - "MarkComSourceInterfacesAsIDispatch"
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1412: Marcar las interfaces ComSource como IDispatch
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkComSourceInterfacesAsIDispatch|  
|Identificador de comprobación|CA1412|  
|Categoría|Microsoft.Interoperability|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo está marcado con el atributo <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> y al menos una de la interfaz especificada no está marcada con el atributo <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> establecido en el valor `InterfaceIsDispatch`.  
  
## Descripción de la regla  
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> se utiliza para identificar las interfaces de eventos que una clase expone a los clientes del Modelo de objetos componentes \(COM\).  Estas interfaces se deben exponer como `InterfaceIsIDispatch` para permitir que los clientes COM de Visual Basic 6 reciban las notificaciones de eventos.  De forma predeterminada, si una interfaz no está marcada con el atributo <xref:System.Runtime.InteropServices.InterfaceTypeAttribute>, se expone como una interfaz dual.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, agregue o modifique el atributo <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> de modo que su valor se establezca en InterfaceIsIDispatch para todas las interfaces especificadas con el atributo <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra una clase donde una de las interfaces infringe la regla.  
  
 [!code-cs[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]  
  
## Reglas relacionadas  
 [CA1408: No utilizar AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)  
  
## Vea también  
 [How to: Raise Events Handled by a COM Sink](http://msdn.microsoft.com/es-es/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)