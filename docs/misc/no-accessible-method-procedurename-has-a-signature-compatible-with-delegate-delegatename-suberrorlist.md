---
title: "Ning&#250;n m&#233;todo accesible &#39;&lt;nombreDeProcedimiento&gt;&#39; tiene una signatura compatible con el delegado &#39;&lt;nombreDeDelegado&gt;&#39;:&lt;sublistaDeErrores&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30950"
  - "vbc30950"
helpviewer_keywords: 
  - "BC30950"
ms.assetid: c1938099-2c03-491e-b599-d0c43bf94baf
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ning&#250;n m&#233;todo accesible &#39;&lt;nombreDeProcedimiento&gt;&#39; tiene una signatura compatible con el delegado &#39;&lt;nombreDeDelegado&gt;&#39;:&lt;sublistaDeErrores&gt;
Una instrucción de asignación asigna la dirección de un procedimiento a una variable de delegado, pero el compilador no encuentra una versión del procedimiento con una signatura coincidente.  
  
 Cuando el código usa la dirección de un procedimiento, el compilador intenta encontrar una versión del procedimiento con una lista de parámetros que coincida con la del delegado. Si el procedimiento está definido en varias versiones sobrecargadas, el compilador intenta encontrar una versión única con una signatura coincidente. Para obtener más información, consulta [Resolución de sobrecargas](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution).  
  
 Si el compilador no encuentra ninguna versión del procedimiento con una signatura coincidente, genera este error. Esto puede ocurrir, por ejemplo, si el procedimiento o el delegado son genéricos y se pasa un argumento de tipo que proporcione una signatura que no coincida con la otra.  
  
 **Identificador de error:** BC30950  
  
### Para corregir este error  
  
1.  Vuelva a definir el procedimiento o el delegado para que tengan listas de parámetros correspondientes.  
  
     O bien  
  
     Defina un nuevo delegado con una lista de parámetros que coincida con la del procedimiento, o bien defina un nuevo procedimiento con una lista de parámetros que coincida con la del delegado.  
  
2.  Si el procedimiento o el delegado son genéricos, páseles un argumento de tipo que haga que su signatura coincida con la otra.  
  
## Vea también  
 [AddressOf \(Operador\)](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [Delegate \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [NO ESTÁ EN LA COMPILACIÓN: Delegados y el operador AddressOf](http://msdn.microsoft.com/es-es/7b2ed932-8598-4355-b2f7-5cedb23ee86f)   
 [Resolución de sobrecargas](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution)   
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)