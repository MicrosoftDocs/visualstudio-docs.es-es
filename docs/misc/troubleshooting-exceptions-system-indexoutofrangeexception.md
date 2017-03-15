---
title: "Soluci&#243;n de problemas de excepciones: System.IndexOutOfRangeException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "IndexOutOfRangeException (clase)"
ms.assetid: 9e28623c-93fc-4111-a0cb-c380e0b5de0c
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.IndexOutOfRangeException
Cuando se intenta obtener acceso a un elemento de una matriz o colección con un índice que se encuentra fuera de los límites de la matriz o que es menor que cero, se produce una excepción <xref:System.IndexOutOfRangeException>.  
  
## Sugerencias asociadas  
 **Asegúrese de que el índice máximo de una lista sea inferior a su tamaño.**  
 El índice máximo de una lista debe ser menor que el tamaño de la lista.  
  
 **Asegúrese de que el índice no es un número negativo.**  
 Esta excepción se producirá si el índice es menor que cero.  
  
 **Asegúrese de que los nombres de la columna de datos son correctos.**  
 Esta excepción se puede producir si el nombre de la columna de datos que se proporciona para la propiedad <xref:System.Data.DataView.Sort%2A?displayProperty=fullName> no es válido. Para obtener más información, vea la clase <xref:System.Data.DataView>.  
  
## Ejemplo  
  
### Descripción  
 En el siguiente ejemplo se utiliza un bloque `Try…Catch` para interceptar `IndexOutOfRangeException` cuando el índice `i` está fuera de los límites de la matriz, 0 a 3. En el ejemplo siguiente se muestra lo siguiente:  
  
 `Element at index 0: 3`  
  
 `Element at index 2: 5`  
  
 `Element at index -1: IndexOutOfRangeException caught`  
  
 `Element at index 4: IndexOutOfRangeException caught`  
  
### Código  
  
```vb#  
Module Module1 Sub Main() ' The first two tests will display the value of the array element. IndexTest(0) IndexTest(2) ' The following two calls will display the information that ' an IndexOutOfRangeException was caught. IndexTest(-1) IndexTest(4) End Sub Sub IndexTest(ByVal i As Integer) Dim testArray() As Integer = {3, 4, 5, 6} Console.Write("Element at index {0}: ", i) Try Console.WriteLine(testArray(i)) Catch ex As IndexOutOfRangeException Console.WriteLine("IndexOutOfRangeException caught") End Try End Sub End Module  
```  
  
## Vea también  
 <xref:System.IndexOutOfRangeException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Matrices](/dotnet/visual-basic/programming-guide/language-features/arrays/index)