---
title: "slice (M&#233;todo, String de JavaScript) | Microsoft Docs"
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
  - "slice (método)"
  - "cadenas [Visual Studio], devolver caracteres"
ms.assetid: 80cd77a6-3718-492e-8e96-f909d8721d91
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# slice (M&#233;todo, String de JavaScript)
Devuelve una sección de una cadena.  
  
## Sintaxis  
  
```  
  
stringObj.slice(start, [end])   
```  
  
## Parámetros  
 `stringObj`  
 Requerido.  Objeto `String` o literal de cadena.  
  
 `start`  
 Requerido.  Índice del principio de la parte especificada de `stringObj`.  
  
 `end`  
 Opcional.  Índice del final de la parte especificada de `stringObj`.  La subcadena incluye los caracteres hasta el carácter indicado por `end`, pero sin incluirlo.  Si este valor no se especifica, la subcadena continúa hasta el final de `stringObj`.  
  
## Comentarios  
 El método `slice` devuelve un objeto `String` que contiene la parte especificada de `stringObj`.  
  
 El método `slice` copia hasta el carácter indicado por `end`, pero sin incluirlo.  
  
 Si `start` es negativo, se trata como *length* \+ `start`, donde *length* es la longitud de la cadena.  Si `end` es negativo, se trata como *length* \+ `end`.  Si se omite `end`, la copia continúa hasta el final de `stringObj`.  Si `end` tiene lugar antes que `start`, no se copian caracteres en la cadena nueva.  
  
## Ejemplo  
 En el primer ejemplo, el método `slice` devuelve la cadena completa.  En el segundo ejemplo, el método `slice` devuelve la cadena completa, a excepción del último carácter.  
  
```javascript  
var str1 = "all good boys do fine";  
  
var slice1 = str1.slice(0);  
var slice2 = str1.slice(0,-1);  
var slice3 = str1.slice(4);  
var slice4 = str1.slice(4, 8);  
  
document.write(slice1 + "<br/>");  
document.write(slice2 + "<br/>");  
document.write(slice3 + "<br/>");  
document.write(slice4);  
  
// Output:  
// all good boys do fine  
// all good boys do fin  
// good boys do fine  
// good  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [String \(Objeto\)](../../javascript/reference/string-object-javascript.md)  
  
## Vea también  
 [slice \(Método, Array\)](../../javascript/reference/slice-method-array-javascript.md)