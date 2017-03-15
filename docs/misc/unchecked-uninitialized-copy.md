---
title: "unchecked_uninitialized_copy | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.unchecked_uninitialized_copy"
  - "unchecked_uninitialized_copy"
  - "std::unchecked_uninitialized_copy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unchecked_uninitialized_copy (función)"
ms.assetid: 38568841-314e-446b-91d0-92cc231e3b3c
caps.latest.revision: 9
caps.handback.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
---
# unchecked_uninitialized_copy
Igual que [uninitialized\_copy](../Topic/uninitialized_copy.md) pero permite el uso de un iterador no comprobado como iterador de salida cuando se define \_SECURE\_SCL\=1. Esta función se define en el [stdext \(Espacio de nombres\)](/visual-cpp/standard-library/stdext-namespace) espacio de nombres.  
  
> [!NOTE]
>  Este algoritmo es una extensión de Microsoft de la Biblioteca estándar de C\+\+. El código implementado mediante este algoritmo no será portable.  
  
## Sintaxis  
  
```  
template<class InputIterator, class ForwardIterator>  
   ForwardIterator unchecked_uninitialized_copy(  
      InputIterator _First,  
      InputIterator _Last,  
      ForwardIterator _Dest  
   );  
  
template<class InputIterator, class ForwardIterator, class Allocator>  
   ForwardIterator unchecked_uninitialized_copy(  
      InputIterator _First,  
      InputIterator _Last,  
      ForwardIterator _Dest,  
      Allocator& _Al  
   );  
```  
  
#### Parámetros  
 `_First`  
 Iterador de entrada que direcciona el primer elemento del intervalo de origen que se va a copiar.  
  
 `_Last`  
 Iterador de entrada que direcciona el último elemento del intervalo de origen que se va a copiar.  
  
 `_Dest`  
 Iterador hacia delante que direcciona el primer elemento del intervalo de destino que se va a copiar.  
  
 `_Al`  
 La clase de asignador que se usa con este objeto.[vector::get\_allocator](../Topic/vector::get_allocator.md) Devuelve la clase de asignador del objeto.  
  
## Valor devuelto  
 Iterador hacia delante que direcciona la posición de un elemento situado más allá del último elemento del intervalo de destino que va a recibir la copia.  
  
## Comentarios  
 Consulte [uninitialized\_copy](../Topic/uninitialized_copy.md) para obtener un ejemplo de código.  
  
 Para obtener más información sobre los iteradores comprobados, vea [Iteradores activados](/visual-cpp/standard-library/checked-iterators).  
  
## Requisitos  
 **Encabezado:** \<memory\>  
  
 **Espacio de nombres:** stdext