---
title: "exec (M&#233;todo, Regular Expression de JavaScript) | Microsoft Docs"
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
  - "exec"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Exec (método)"
  - "coincidencia de cadenas"
ms.assetid: 83092452-60cc-4218-b4ae-af9e3cb96c34
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# exec (M&#233;todo, Regular Expression de JavaScript)
Ejecuta una búsqueda en una cadena mediante un patrón de expresión regular y devuelve una matriz que contiene los resultados de la búsqueda.  
  
## Sintaxis  
  
```  
  
rgExp.exec(str)   
```  
  
## Parámetros  
 `rgExp`  
 Obligatorio.  Instancia de un objeto **Regular Expression** que contiene el patrón de expresión regular y las marcas aplicables.  
  
 `str`  
 Obligatorio.  Objeto `String` o literal de cadena donde se realizará la búsqueda.  
  
## Comentarios  
 Si el método `exec` no encuentra ninguna coincidencia, devuelve `null`.  Si encuentra una coincidencia, `exec` devuelve una matriz y las propiedades del objeto global `RegExp` se actualizan para reflejar los resultados de la búsqueda.  El elemento cero de la matriz contiene toda la coincidencia, mientras que los elementos 1 a *n* contienen las subcoincidencias que se producen dentro de la coincidencia.  El comportamiento es idéntico al del método `match` sin establecer la marca global \(**g**\).  
  
 Si se establece la marca global para una expresión regular, el método `exec` busca la cadena empezando en la posición indicada por el valor de `lastIndex`.  Si no se establece la marca global, `exec` omite el valor de `lastIndex` y busca desde el principio de la cadena.  
  
 La matriz devuelta por el método `exec` tiene tres propiedades: **input**, **index** y **lastIndex**. La propiedad **input** contiene la cadena completa en la que se busca.  La propiedad **index** contiene la posición de la subcadena coincidente dentro de la cadena completa en la que se busca.  La propiedad `lastIndex` contiene la posición siguiente al último carácter de la coincidencia.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `exec`:  
  
```javascript  
function RegExpTest()  
{  
   var ver = Number(ScriptEngineMajorVersion() + "." + ScriptEngineMinorVersion())  
   if (ver < 5.5)  
   {  
      document.write("You need a newer version of JavaScript for this to work");  
      return;  
   }  
  
   var src = "The quick brown fox jumps over the lazy dog.";  
  
   // Create regular expression pattern with a global flag.  
   var re = /\w+/g;  
  
   // Get the next word, starting at the position of lastindex.  
   var arr;  
   while ((arr = re.exec(src)) != null)  
      {  
      // New line:  
      document.write ("<br />");    
      document.write (arr.index + "-" + arr.lastIndex + " ");  
      document.write (arr[0]);  
      }  
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Regular Expression \(Objeto\)](../../javascript/reference/regular-expression-object-javascript.md)  
  
## Vea también  
 [match \(Método, String\)](../../javascript/reference/match-method-string-javascript.md)   
 [RegExp \(Objeto\)](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/es-es/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [search \(Método, String\)](../../javascript/reference/search-method-string-javascript.md)   
 [test \(Método, Regular Expression\)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Regular Expression Programming \(JavaScript\)](http://msdn.microsoft.com/es-es/3b62e27c-4f07-4726-a95b-6e841807bfaf)