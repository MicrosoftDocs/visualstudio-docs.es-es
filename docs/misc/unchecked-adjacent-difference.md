---
title: "unchecked_adjacent_difference | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.unchecked_adjacent_difference"
  - "std::unchecked_adjacent_difference"
  - "unchecked_adjacent_difference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unchecked_adjacent_difference (función)"
ms.assetid: 3a6b0b49-a84b-40b1-bcd5-3bf76c6ef7d7
caps.latest.revision: 14
caps.handback.revision: 14
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
---
# unchecked_adjacent_difference
Igual que [adjacent\_difference](../Topic/adjacent_difference.md), pero permite el uso de un iterador no comprobado como iterador de salida cuando \_SECURE\_SCL \= 1 está definido.`unchecked_adjacent_difference` se define en el `stdext` espacio de nombres.  
  
> [!NOTE]
>  Este algoritmo es una extensión de Microsoft de la Biblioteca estándar de C\+\+. El código implementado mediante este algoritmo no será portable.  
  
## Sintaxis  
  
```  
template<class InputIterator, class OutIterator>  
   OutputIterator unchecked_adjacent_difference(  
      InputIterator_First,  
      InputIterator _Last,  
      OutputIterator_Result   
   );  
  
template<class InputIterator, class OutputIterator, class BinaryOperation>  
   OutputIterator unchecked_adjacent_difference(  
      InputIterator_First,  
      InputIterator _Last,  
      OutputIterator_Result,   
      BinaryOperation _Binary_op  
   );  
```  
  
#### Parámetros  
 `_First`  
 Iterador de entrada que direcciona el primer elemento del intervalo de entrada cuyos elementos se van a diferenciar con sus predecesores respectivos o donde se va a actuar sobre el par de valores mediante otra operación binaria especificada.  
  
 `_Last`  
 Iterador de entrada que direcciona el último elemento del intervalo de entrada cuyos elementos se van a diferenciar con sus predecesores respectivos o donde se va a actuar sobre el par de valores mediante otra operación binaria especificada.  
  
 `_Result`  
 Iterador de salida que direcciona el primer elemento de un intervalo de destino donde se va a almacenar la serie de diferencias o los resultados de la operación especificada.  
  
 `_Binary_op`  
 Operación binaria que se va a aplicar en la operación generalizada reemplazando la operación de resta en el procedimiento de diferenciación.  
  
## Valor devuelto  
 Un iterador de salida que direcciona al final del intervalo de destino: `_Result` \+ \(`_Last` \- `_First`\).  
  
## Comentarios  
 Consulte [adjacent\_difference](../Topic/adjacent_difference.md) para obtener un ejemplo de código.  
  
 Para obtener más información sobre los iteradores comprobados, vea [Iteradores activados](/visual-cpp/standard-library/checked-iterators).  
  
## Requisitos  
 **Encabezado:** \<numeric\>  
  
 **Espacio de nombres:** stdext  
  
## Vea también  
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)