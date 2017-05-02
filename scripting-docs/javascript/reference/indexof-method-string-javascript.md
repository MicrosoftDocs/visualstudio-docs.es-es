---
title: "indexOf (M&#233;todo, String de JavaScript) | Microsoft Docs"
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
  - "indexOf"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "indexOf (método), cadena"
  - "cadena, indexOf (método)"
ms.assetid: a17372fa-669b-471b-9240-46927a265152
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# indexOf (M&#233;todo, String de JavaScript)
Devuelve la posición de la primera repetición de una subcadena.  
  
## Sintaxis  
  
```  
  
strObj. indexOf(subString[, startIndex])  
```  
  
## Parámetros  
 `strObj`  
 Obligatorio.  Objeto `String` o literal de cadena.  
  
 `subString`  
 Obligatorio.  La subcadena que se va a buscar en la cadena.  
  
 `startIndex`  
 Opcional.  Índice en el que va a comenzar la búsqueda del objeto `String`.  Si se omite, la búsqueda comienza al principio de la cadena.  
  
## Comentarios  
 El método **indexOf** devuelve el comienzo de la subcadena en el objeto `String`.  Si la subcadena no se encuentra, se devuelve \-1.  
  
 Si `startindex` es negativo, `startindex` se trata como cero.  Si es mayor que el índice más alto, se trata como el índice más alto.  
  
 La búsqueda se realiza de izquierda a derecha.  De lo contrario, este método es idéntico a **lastIndexOf**.  
  
## Ejemplo  
 El siguiente ejemplo muestra el uso del método **indexOf**.  
  
```javascript  
var str = "original equipment manufacturer";  
  
var s = "equip is at position " + str.indexOf("equip");  
s += "<br />";  
s += "abc is at position " + str.indexOf("abc");  
  
document.write(s);  
  
// Output:  
// equip is at position 9  
// abc is at position -1  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [String \(Objeto\)](../../javascript/reference/string-object-javascript.md)  
  
## Vea también  
 [lastIndexOf \(Método, String\)](../../javascript/reference/lastindexof-method-string-javascript.md)   
 [Aplicación de ejemplo de desplazamiento, movimiento panorámico y zoom](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)