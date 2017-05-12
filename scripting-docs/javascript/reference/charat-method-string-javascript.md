---
title: "charAt (M&#233;todo, String de JavaScript) | Microsoft Docs"
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
  - "charAt"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "objeto String, devolver caracteres"
  - "charAt (método)"
  - "caracteres, devolver parte de"
ms.assetid: 63173e15-17f6-47c5-8f94-98ef1eb04c1a
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# charAt (M&#233;todo, String de JavaScript)
Devuelve el carácter que se encuentra en el índice especificado.  
  
## Sintaxis  
  
```  
  
strObj. charAt(index)  
```  
  
## Parámetros  
 `strObj`  
 Obligatorio.  Cualquier objeto `String` o literal de cadena.  
  
 `index`  
 Obligatorio.  El índice de base cero del carácter deseado.  
  
## Comentarios  
 El método `charAt` devuelve un valor de carácter igual al carácter situado en la posición especificada por `index`.  El primer carácter de una cadena está en el índice 0, el segundo en el índice 1 y así sucesivamente.  Los valores de `index` que no están dentro del intervalo válido devuelven una cadena vacía.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `charAt`:  
  
```javascript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";  
document.write(str.charAt(str.length - 1));  
  
// Output: Z  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [String \(Objeto\)](../../javascript/reference/string-object-javascript.md)  
  
## Vea también  
 [String \(Objeto\)](../../javascript/reference/string-object-javascript.md)