---
title: "lastIndexOf (M&#233;todo, String de JavaScript) | Microsoft Docs"
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
  - "lastIndexOf"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Método lastIndexOf, cadena"
  - "cadena, método lastIndexOf"
ms.assetid: 1ed36ccd-0f0b-4f16-be45-0567207670af
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# lastIndexOf (M&#233;todo, String de JavaScript)
Devuelve la última repetición de una subcadena en la cadena.  
  
## Sintaxis  
  
```  
  
strObj.lastIndexOf(substring[, startindex])  
```  
  
## Parámetros  
 `strObj`  
 Obligatorio.  Objeto `String` o literal de cadena.  
  
 `substring`  
 Obligatorio.  La subcadena que se va a buscar.  
  
 `startindex`  
 Opcional.  Índice en el que se va a empezar la búsqueda.  Si se omite, la búsqueda comienza al final de la cadena.  
  
## Comentarios  
 El método **lastIndexOf** devuelve un valor entero que indica el principio de la subcadena dentro del objeto `String`.  Si no se encuentra la subcadena, se devuelve \-1.  
  
 Si `startindex` es negativo, `startindex` se trata como cero.  Si es superior al mayor índice de posición de carácter, se trata como el mayor índice posible.  
  
 La búsqueda se realiza empezando en el último carácter de la cadena.  Si no, este método es idéntico a **indexOf**.  
  
 En el siguiente ejemplo se muestra el uso del método **lastIndexOf**.  
  
```javascript  
var str = "time, time";  
  
var s = "";  
s += "time is at position " + str.lastIndexOf("time");  
s += "<br />";  
s += "abc is at position " + str.lastIndexOf("abc");  
  
document.write(s);  
  
// Output:  
// time is at position 6  
// abc is at position -1  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [String \(Objeto\)](../../javascript/reference/string-object-javascript.md)  
  
## Vea también  
 [indexOf \(Método, String\)](../../javascript/reference/indexof-method-string-javascript.md)