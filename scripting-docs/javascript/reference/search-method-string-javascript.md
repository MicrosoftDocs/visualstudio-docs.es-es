---
title: "search (M&#233;todo, String, JavaScript) | Microsoft Docs"
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
  - "search"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "search (método)"
ms.assetid: 1cae0fbc-3319-4327-ba4e-d5fa2c4a9ba0
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# search (M&#233;todo, String, JavaScript)
Busca la primera coincidencia de subcadena en una búsqueda de expresiones regulares.  
  
## Sintaxis  
  
```  
  
stringObj.search(rgExp)   
```  
  
## Parámetros  
 `stringObj`  
 Obligatorio.  Objeto `String` o literal de cadena donde se realizará la búsqueda.  
  
 `rgExp`  
 Obligatorio.  Instancia de un objeto **Regular Expression** que contiene el patrón de expresión regular y las marcas aplicables.  
  
## Valor devuelto  
 Si se encuentra una coincidencia, el método **search** devuelve un valor entero que indica el desplazamiento desde el principio de la cadena en la que se encontró la primera coincidencia.  Si no se encuentra ninguna coincidencia, devuelve \-1.  
  
## Comentarios  
 También puedes establecer la marca `i` que hace que la búsqueda no distinga entre mayúsculas y minúsculas.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra el uso del método **search**.  
  
```javascript  
var src = "is but a Dream within a dream";  
var re = /dream/;  
var pos = src.search(re);  
document.write(pos);  
document.write("<br/>");  
  
re = /dream/i;  
pos = src.search(re);  
document.write(pos);  
  
// Output:   
// 24   
// 9  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [String \(Objeto\)](../../javascript/reference/string-object-javascript.md)  
  
## Vea también  
 [exec \(Método, Regular Expression\)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [match \(Método, String\)](../../javascript/reference/match-method-string-javascript.md)   
 [Regular Expression \(Objeto\)](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/es-es/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [replace \(Método, String\)](../../javascript/reference/replace-method-string-javascript.md)   
 [test \(Método, Regular Expression\)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Regular Expression Programming \(JavaScript\)](http://msdn.microsoft.com/es-es/3b62e27c-4f07-4726-a95b-6e841807bfaf)