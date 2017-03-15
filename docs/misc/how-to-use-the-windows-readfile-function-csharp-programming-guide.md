---
title: "C&#243;mo: Utilizar la funci&#243;n ReadFile de Windows (Gu&#237;a de programaci&#243;n de C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ReadFile (función) [C#]"
ms.assetid: 46bb53e0-a658-48c9-ae36-6720da7781c1
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "billchi"
manager: "douge"
---
# C&#243;mo: Utilizar la funci&#243;n ReadFile de Windows (Gu&#237;a de programaci&#243;n de C#)
Este ejemplo muestra la función de Windows `ReadFile` que lee y muestra un archivo de texto.  La función `ReadFile` requiere el uso de código `unsafe` porque requiere un puntero como parámetro.  
  
 La matriz de bytes pasada a la función `Read` es un tipo administrado.  Esto significa que el recolector de elementos no utilizados de Common Language Runtime \(CLR\) puede reubicar la memoria usada por la matriz según lo considere necesario.  Para evitar esto, se utiliza [fixed](/dotnet/csharp/language-reference/keywords/fixed-statement) para obtener un puntero a la memoria y marcarlo para que no lo mueva el recolector de elementos no utilizados.  Al final del bloque `fixed`, la memoria vuelve automáticamente a estar sujeta a moverse a través de la recolección de elementos no utilizados.  
  
 Esta capacidad se conoce como *anclaje declarativo*.  Con el anclaje apenas hay carga de ejecución, a menos que se produzca una recolección de elementos no utilizados en el bloque `fixed`, lo cual no es probable que suceda.  Sin embargo, el anclaje puede producir algunos efectos secundarios no deseados durante la ejecución de la recolección de elementos no utilizados global.  Los búferes anclados limitan considerablemente la capacidad del recolector de elementos no utilizados para compactar la memoria.  Por consiguiente, el anclaje debería evitarse si es posible.  
  
## Ejemplo  
 [!code-cs[csProgGuidePointers#2](../misc/codesnippet/CSharp/how-to-use-the-windows-readfile-function-csharp-programming-guide_1.cs)]  
  
## Vea también  
 [Guía de programación de C\#](/dotnet/csharp/programming-guide/index)   
 [Referencia de C\#](/dotnet/csharp/language-reference/index)   
 [Código no seguro y punteros](/dotnet/csharp/programming-guide/unsafe-code-pointers/index)   
 [Tipos de puntero](/dotnet/csharp/programming-guide/unsafe-code-pointers/pointer-types)   
 [Garbage Collection](../Topic/Garbage%20Collection.md)