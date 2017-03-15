---
title: "El m&#233;todo de extensi&#243;n &#39;&lt;nombreM&#233;todo&#39; tiene restricciones de tipo que no se pueden cumplir nunca. | Microsoft Docs"
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
  - "bc36561"
  - "vbc36561"
helpviewer_keywords: 
  - "BC36561"
ms.assetid: ff42d6e9-611b-407d-a269-f268b36ed277
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El m&#233;todo de extensi&#243;n &#39;&lt;nombreM&#233;todo&#39; tiene restricciones de tipo que no se pueden cumplir nunca.
Los parámetros de tipo de este método interactúan de forma que les impide que alguna vez se cumplan. El siguiente método de extensión es un ejemplo.  
  
```  
'' Not valid. '<Extension()> _ 'Sub extensionExample(Of T As U, U)(ByVal para1 As T, ByVal para2 As U) 'End Sub  
```  
  
 Dado que el método es un método de extensión, el compilador debe ser capaz de determinar el tipo o tipos de datos que el método extiende basándose únicamente en el primer parámetro de la declaración de método, `para1`, y el argumento enviado para ese parámetro. Cuando el primer parámetro hace referencia a parámetros de tipo genérico, `para1 as T`, las restricciones en los parámetros genéricos restringen el conjunto de tipos al que se aplica el método.  
  
 La aplicabilidad de un método de extensión se determina a partir del argumento proporcionado para el primer parámetro, que es `arg1` en el código siguiente.  
  
 `'' Not valid.`  
  
 `'arg1.extensionExample(arg2)`  
  
 Debe ser posible comprobar las restricciones en todos los parámetros de tipo genérico que hace referencia el primer parámetro, `para1`, examinando solo el primer argumento, `arg1`. En `extensionExample`, no se puede determinar el conjunto de tipos que se extiende a partir del primer parámetro solo. Parámetro de tipo `T` está restringido por el parámetro de tipo `U`, al que `para1` no hace referencia y que no se puede inferir de `arg1`. Por lo tanto, no se puede comprobar la aplicabilidad del método a cualquier tipo posible y nunca se puede llamar al método.  
  
 **Identificador de error:** BC36561  
  
### Para corregir este error  
  
-   Cambie la declaración de tipo para eliminar la interdependencia entre los tipos.  
  
## Vea también  
 [métodos de extensión.](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)