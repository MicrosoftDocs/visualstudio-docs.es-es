---
title: "CA1033: Los tipos secundarios deber&#237;an poder llamar a los m&#233;todos de interfaz | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "InterfaceMethodsShouldBeCallableByChildTypes"
  - "CA1033"
helpviewer_keywords: 
  - "CA1033"
  - "InterfaceMethodsShouldBeCallableByChildTypes"
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1033: Los tipos secundarios deber&#237;an poder llamar a los m&#233;todos de interfaz
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|  
|Identificador de comprobación|CA1033|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un tipo no sellado visible externamente proporciona un método explícito de implementación de una interfaz pública pero no proporciona un método visible externamente alternativo con el mismo nombre.  
  
## Descripción de la regla  
 Tiene en cuenta un tipo base que implementa explícitamente un método de interfaz público.  Un tipo que deriva de un tipo base solo puede obtener acceso al método de interfaz heredado a través de una referencia a la instancia actual \(`this` en C\#\) que se convierte en la interfaz.  Si el tipo derivado vuelve a implementar \(explícitamente\) el método de interfaz heredado, ya no se podrá obtener acceso a la implementación base.  La llamada a través de la referencia de la instancia actual invocará la implementación derivada; esto produce recursividad y, finalmente, un desbordamiento de pila.  
  
 Esta regla no crea informe sobre la infracción para una implementación explícita de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> cuando se proporciona un método `Close()` o `System.IDisposable.Dispose(Boolean)` visible externamente.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, implemente un método nuevo que exponga la misma funcionalidad y sea visible para tipos derivados o cámbielo a una implementación no explícita.  Si se puede realizar un cambio de interrupción, una alternativa es establecer el tipo como sellado.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si se proporciona un método visible externamente que tenga la misma funcionalidad pero con un nombre distinto al del método implementado explícitamente.  
  
## Ejemplo  
 El ejemplo siguiente muestra un tipo, `ViolatingBase`, que infringe la regla y un tipo, `FixedBase`, que muestra una corrección de la infracción.  
  
 [!code-cs[FxCop.Design.ExplicitMethodImplementations#1](../code-quality/codesnippet/CSharp/ca1033-interface-methods-should-be-callable-by-child-types_1.cs)]  
  
## Vea también  
 [Interfaces](/dotnet/csharp/programming-guide/interfaces/index)