---
title: "No se pueden usar miembros de instancia ni &#39;Me&#39; en una expresi&#243;n de consulta. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36535"
  - "bc36535"
helpviewer_keywords: 
  - "BC36535"
ms.assetid: afb5281b-70a7-48c7-a46d-39522b96b1ff
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se pueden usar miembros de instancia ni &#39;Me&#39; en una expresi&#243;n de consulta.
Una consulta LINQ en una `Structure` incluye una referencia a `Me` o a un miembro de instancia de la estructura. Las referencias a `Me` o a los miembros de instancia no se permiten en expresiones de consulta dentro de un `Structure`.  
  
 **Identificador de error:** BC36535  
  
### Para corregir este error  
  
1.  Cree una copia del miembro de instancia o el valor devuelto por la referencia a `Me` y use la copia en la expresión de consulta, como se muestra en el ejemplo siguiente.  
  
    ```vb#  
    Structure SampleStructure Public SearchValue As Integer Public Sub SetSearchValue(ByVal number As Integer) SearchValue = number End Sub Public Sub GetData() Dim sv = SearchValue Dim SampleData = New Integer() {1, 2, 3, 4} Dim query = From number In SampleData _ Where number < sv End Sub End Structure  
    ```  
  
## Vea también  
 [Introducción a LINQ en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)   
 [Me](http://msdn.microsoft.com/es-es/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [Estructura \(Visual Basic\)](http://msdn.microsoft.com/es-es/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)