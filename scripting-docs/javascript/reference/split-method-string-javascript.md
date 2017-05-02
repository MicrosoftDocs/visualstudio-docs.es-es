---
title: "split (M&#233;todo, String de JavaScript) | Microsoft Docs"
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
  - "split"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "split (método)"
ms.assetid: 7f093336-c887-4efb-b91f-819b6d18a181
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# split (M&#233;todo, String de JavaScript)
Divide una cadena en subcadenas mediante el separador especificado y las devuelve como una matriz.  
  
## Sintaxis  
  
```  
  
stringObj.split([separator[, limit]])  
```  
  
## Parámetros  
 `stringObj`  
 Obligatorio.  Objeto `String` o literal de cadena que se va a dividir.  El método **split** no modifica este objeto.  
  
 `separator`  
 Opcional.  Cadena u objeto **Regular Expression** que identifica uno o varios caracteres que se van a usar para separar la cadena.  Si se omite, se devuelve una matriz de un único elemento que contiene toda la cadena.  
  
 `limit`  
 Opcional.  Valor utilizado para limitar el número de elementos devueltos en la matriz.  
  
## Valor devuelto  
 El resultado del método **split** es una matriz de cadenas dividida en cada punto donde aparece `separator` en `stringObj`.  El argumento `separator` no se devuelve como parte de ningún elemento de la matriz.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra el uso del método **split**.  
  
```javascript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.split(" ");  
for (var i in ss) {  
    document.write(ss[i]);  
    document.write("<br/>");  
}  
  
// Output:   
// The  
// quick  
// brown  
// fox  
// jumps  
// over  
// the  
// lazy  
// dog.  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [String \(Objeto\)](../../javascript/reference/string-object-javascript.md)  
  
## Vea también  
 [concat \(Método, String\)](../../javascript/reference/concat-method-string-javascript.md)   
 [RegExp \(Objeto\)](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression \(Objeto\)](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/es-es/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Aplicación de ejemplo de desplazamiento, movimiento panorámico y zoom](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)