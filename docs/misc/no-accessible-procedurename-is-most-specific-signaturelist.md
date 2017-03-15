---
title: "&#39;&lt;nombreProcedimiento&gt;&#39; no accesible es m&#225;s espec&#237;fico: &lt;listaFirmas&gt; | Microsoft Docs"
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
  - "vbc30794"
  - "BC30794"
helpviewer_keywords: 
  - "BC30794"
ms.assetid: 51d54cbb-b530-4661-9952-5ccc17e4220b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nombreProcedimiento&gt;&#39; no accesible es m&#225;s espec&#237;fico: &lt;listaFirmas&gt;
Una instrucción de asignación asigna la dirección de un procedimiento sobrecargado a una variable de delegado, pero el compilador no puede resolver entre las versiones sobrecargadas.  
  
 Cuando el código usa la dirección de un procedimiento que está definido en varias versiones sobrecargadas, el compilador debe decidir cuál de las sobrecargas debe usar. Intenta encontrar una única versión con una lista de parámetros que coincida con la lista de parámetros de delegado. Para obtener más información, consulta [Resolución de sobrecargas](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution).  
  
 Si el compilador encuentra más de una versión del procedimiento con una firma que coincide, genera este error. Esto puede ocurrir, por ejemplo, si una de las sobrecargas es genérica y se pasa un argumento de tipo que le da una firma idéntica a la de otra sobrecarga.  
  
 **Identificador de error:** BC30794  
  
### Para corregir este error  
  
-   Si el conflicto se produce por una sobrecarga genérica que tiene la misma firma que otra sobrecarga, cambie el argumento de tipo que se ha pasado a esa sobrecarga genérica.  
  
## Vea también  
 [AddressOf \(Operador\)](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [Delegate \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [NO ESTÁ EN LA COMPILACIÓN: Delegados y el operador AddressOf](http://msdn.microsoft.com/es-es/7b2ed932-8598-4355-b2f7-5cedb23ee86f)   
 [Resolución de sobrecargas](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution)   
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)