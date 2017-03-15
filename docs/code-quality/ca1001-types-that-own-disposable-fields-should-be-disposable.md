---
title: "CA1001: Los tipos que poseen campos descartables deben ser descartables | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1001"
  - "TypesThatOwnDisposableFieldsShouldBeDisposable"
helpviewer_keywords: 
  - "CA1001"
  - "TypesThatOwnDisposableFieldsShouldBeDisposable"
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 22
---
# CA1001: Los tipos que poseen campos descartables deben ser descartables
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|  
|Identificador de comprobación|CA1001|  
|Categoría|Microsoft.Design|  
|Cambio problemático|No problemático: si el tipo no es visible fuera del ensamblado.<br /><br /> Problemático: si el tipo es visible fuera del ensamblado.|  
  
## Motivo  
 Una clase declara e implementa un campo de instancia que es un tipo <xref:System.IDisposable?displayProperty=fullName> y la clase no implementa <xref:System.IDisposable>.  
  
## Descripción de la regla  
 Una clase implementa la interfaz <xref:System.IDisposable> para desechar recursos no administrados que posee.  Un campo de instancia que es un tipo <xref:System.IDisposable> indica que el campo posee un recurso no administrado.  Una clase que declara un campo <xref:System.IDisposable> posee indirectamente un recurso no administrado y debería implementar la interfaz <xref:System.IDisposable>.  Si la clase no posee directamente ningún recurso no administrado, no debe implementar un finalizador.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, implemente <xref:System.IDisposable> y, desde el método <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>, llame al método <xref:System.IDisposable.Dispose%2A> del campo.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 El ejemplo siguiente muestra una clase que infringe la regla y otra que la cumple implementando <xref:System.IDisposable>.  La clase no implementa un finalizador porque no posee directamente ningún recurso no administrado.  
  
 [!code-vb[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/VisualBasic/ca1001-types-that-own-disposable-fields-should-be-disposable_1.vb)]
 [!code-cs[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/CSharp/ca1001-types-that-own-disposable-fields-should-be-disposable_1.cs)]  
  
## Reglas relacionadas  
 [CA2213: Aplique Dispose a los campos a los que se pueda](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
 [CA2216: Los tipos descartables deben declarar el finalizador](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
 [CA2215: Los métodos Dispose deben llamar a Dispose de clase base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA1049: Los tipos que poseen recursos nativos deben ser descartables](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)