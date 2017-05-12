---
title: "substring (M&#233;todo, String de JavaScript) | Microsoft Docs"
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
  - "substring"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "subcadenas"
  - "substring (método)"
ms.assetid: 9cf9a005-cbe3-42fd-828b-57a39f54224c
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# substring (M&#233;todo, String de JavaScript)
Devuelve la subcadena de la ubicación especificada dentro de un objeto `String`.  
  
## Sintaxis  
  
```  
  
      strVariable. substring(start [, end])  
"String Literal".substring(start [, end])   
```  
  
## Parámetros  
 `start`  
 Obligatorio.  Entero correspondiente al índice basado en cero que indica el principio de la subcadena.  
  
 `end`  
 Opcional.  Entero correspondiente al índice basado en cero que indica el final de la subcadena.  La subcadena incluye los caracteres hasta el carácter indicado por `end`, pero sin incluirlo.  
  
 Si se omite `end`, se devuelven los caracteres comprendidos entre `start` y el final de la cadena original.  
  
## Comentarios  
 El método `substring` devuelve una cadena que contiene la subcadena desde `start` hasta `end`, pero sin incluirlo.  
  
 El método **substring** usa el menor valor de `start` y `end` como punto inicial de la subcadena.  Por ejemplo, strvar.substring\(0, 3**\)** y strvar.substring\(3, 0\) devuelven la misma subcadena.  
  
 Si `start` o `end` es `NaN` o es negativo, se reemplaza con cero.  
  
 La longitud de la subcadena es igual al valor absoluto de la diferencia entre `start` y `end`.  Por ejemplo, la longitud de la subcadena devuelta en strvar.substring\(0, 3\) y strvar.substring\(3, 0\) es tres.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método **substring**.  
  
```javascript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substring(10, 15);  
document.write(ss);  
  
// Output:  
// brown  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [substr \(Método, String\)](../../javascript/reference/substr-method-string-javascript.md)