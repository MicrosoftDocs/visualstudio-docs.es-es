---
title: "match (M&#233;todo, String de JavaScript) | Microsoft Docs"
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
  - "match"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Match (método)"
ms.assetid: eda9ad27-4f9b-4cb1-8345-a0ae85979ca0
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# match (M&#233;todo, String de JavaScript)
Compara una cadena con una expresión regular y devuelve una matriz que contiene los resultados de la búsqueda.  
  
## Sintaxis  
  
```  
  
stringObj.match(rgExp)   
```  
  
## Parámetros  
 `stringObj`  
 Requerido.  Objeto `String` o literal de cadena donde se realizará la búsqueda.  
  
 `rgExp`  
 Requerido.  Un objeto de expresión regular que contiene el patrón de expresión regular y las marcas aplicables.  Estos también puede ser un nombre de variable o un literal de cadena que contenga el patrón de expresión regular y las marcas.  
  
## Comentarios  
 Si el método `match` no encuentra ninguna coincidencia, devuelve `null`.  Si encuentra una coincidencia, el método `match` devuelve una matriz y las propiedades del objeto global `RegExp` se actualizan para reflejar los resultados de la búsqueda.  
  
 Si no se establece la marca global \(`g`\), el elemento cero de la matriz contiene toda la coincidencia, mientras que los elementos del 1 al *n* contienen las subcoincidencias.  Este comportamiento es idéntico al de [exec \(Método, Regular Expression\)](../../javascript/reference/exec-method-regular-expression-javascript.md) cuando no se establece la marca global.  Si se establece la marca global, los elementos del 0 al *n* contienen todas las coincidencias que se hayan encontrado.  
  
 Si la marca global no se establece, la matriz devuelta por el método `match` tiene dos propiedades, `input` y `index`.  La propiedad `input` contiene la cadena completa en que se busca.  La propiedad `index` contiene la posición de la subcadena coincidente dentro de la cadena completa en que se busca.  
  
 Si se establece la marca `i`, la búsqueda no distingue mayúsculas de minúsculas.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `match`.  
  
```javascript  
var src = "azcafAJAC";  
  
var re = /[a-c]/;  
  
var result = src.match(re);  
  
// The entire match is in array element 0.  
document.write(result[0] + "<br/>");  
  
// Now try the same match with the global flag.  
var reg = /[a-c]/g;  
result = src.match(reg);  
  
// The matches are in elements 0 through n.  
for (var index = 0; index < result.length; index++)  
{  
    document.write ("submatch " + index + ": " +  result[index]);  
    document.write("<br />");  
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [String \(Objeto\)](../../javascript/reference/string-object-javascript.md)  
  
## Vea también  
 [exec \(Método, Regular Expression\)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [RegExp \(Objeto\)](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression \(Objeto\)](../../javascript/reference/regular-expression-object-javascript.md)   
 [replace \(Método, String\)](../../javascript/reference/replace-method-string-javascript.md)   
 [search \(Método, String\)](../../javascript/reference/search-method-string-javascript.md)   
 [test \(Método, Regular Expression\)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Regular Expression Programming \(JavaScript\)](http://msdn.microsoft.com/es-es/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [Alternation and Subexpressions \(JavaScript\)](http://msdn.microsoft.com/es-es/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [Backreferences \(JavaScript\)](http://msdn.microsoft.com/es-es/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)