---
title: "Soluci&#243;n de problemas de excepciones: System.ArgumentException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ArgumentException (excepción)"
  - "System.ArgumentException (excepción)"
ms.assetid: d8052e62-bc73-4828-87e9-a84ef2a39a5b
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.ArgumentException
Se produce una excepción <xref:System.ArgumentException> cuando al menos uno de los argumentos proporcionados a un método no cumple las característica técnicas de los parámetros del método.  
  
 En el ejemplo siguiente, la excepción se produce cuando el argumento enviado al método `DivideByTwo` no es un número par.  
  
```vb#  
Module Module1 Sub Main() ' ArgumentException is not thrown in DivideByTwo because 10 is ' an even number. Console.WriteLine("10 divided by 2 is {0}", DivideByTwo(10)) Try ' ArgumentException is thrown in DivideByTwo because 7 is ' not an even number. Console.WriteLine("7 divided by 2 is {0}", DivideByTwo(7)) Catch argEx As ArgumentException ' Tell the user which problem is encountered. Console.WriteLine("7 cannot be evenly divided by 2.") Console.WriteLine("Exception message: " & argEx.Message) End Try ' Uncomment the next statement to see what happens if you call ' DivideByTwo directly. 'Console.WriteLine(DivideByTwo(7)) End Sub Function DivideByTwo(ByVal num As Integer) As Integer ' If num is an odd number, throw an ArgumentException. The ' ArgumentException class provides a number of constructors ' that you can choose from. If num Mod 2 = 1 Then Throw New ArgumentException("Argument for num must be" & _ " an even number.") End If ' Value of num is even, so return half of its value. Return num / 2 End Function End Module  
```  
  
 Todas las instancias de la clase `ArgumentException` deberían incluir información que especifique qué argumento no es válido y cuál es el intervalo de valores aceptables. Si una excepción más precisa, como <xref:System.ArgumentNullException> o <xref:System.ArgumentOutOfRangeException>, describe mejor la situación, se debería utilizar en lugar de `ArgumentException`.  
  
 Para obtener más información sobre esta excepción, incluidos ejemplos en otros lenguajes, vea <xref:System.ArgumentException>. Para obtener una lista de los constructores adicionales, vea <xref:System.ArgumentException.%23ctor%2A>.  
  
## Vea también  
 <xref:System.ArgumentException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)