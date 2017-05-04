---
title: "slice (M&#233;todo, Array de JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "slice"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "índice basado en cero"
  - "Array (objeto)"
  - "slice (método)"
ms.assetid: 3c122219-14de-4126-b091-809659c026d6
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# slice (M&#233;todo, Array de JavaScript)
Devuelve una sección de una matriz.  
  
## Sintaxis  
  
```  
  
arrayObj.slice(start, [end])   
```  
  
## Parámetros  
 `arrayObj`  
 Obligatorio.  Objeto `Array`.  
  
 `start`  
 Obligatorio.  Principio de la parte especificada de `arrayObj`.  
  
 `end`  
 Opcional.  Final de la parte especificada de `arrayObj`.  
  
## Comentarios  
 El método `slice` devuelve un objeto `Array` que contiene la parte especificada de `arrayObj`.  
  
 El método `slice` copia hasta el elemento indicado por `end`, pero sin incluirlo.  Si el valor de `start` es negativo, se trata como `length` \+ `start`, donde `length` es la longitud de la matriz.  Si el valor de `end` es negativo, se trata como `length` \+ `end`, donde `length` es la longitud de la matriz.  Si se omite `end`, la extracción continúa hasta el final de `arrayObj`.  Si `end` tiene lugar antes que `start`, no se copia ningún elemento en la nueva matriz.  
  
## Ejemplo  
 En los siguientes ejemplos se muestra cómo usar el método `slice`.  En el primer ejemplo, se copian en `newArray` todos los elementos de `myArray` menos el último.  En el segundo ejemplo, solo se copian en `newArray` los dos últimos elementos de `myArray`.  
  
```javascript  
var origArray = [3, 5, 7, 9];  
var newArray = origArray. slice(0, -1);  
document.write(origArray);  
document.write("<br/>");  
newArray = origArray. slice(-2);  
document.write(newArray);  
  
// Output:  
// 3,5,7,9  
// 7,9  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Vea también  
 [slice \(Método, String\)](../../javascript/reference/slice-method-string-javascript.md)   
 [String \(Objeto\)](../../javascript/reference/string-object-javascript.md)