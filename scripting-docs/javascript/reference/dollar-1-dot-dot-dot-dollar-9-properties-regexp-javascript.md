---
title: "$1...$9 (Propiedades,RegExp de JavaScript) | Microsoft Docs"
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
  - "$1...$9"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "$1...$9 (propiedades)"
ms.assetid: 8bd84851-f62f-4eb1-a93d-b67135ea091a
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# $1...$9 (Propiedades,RegExp de JavaScript)
Devuelve las nueve partes memorizadas más recientemente que se encontraron durante la coincidencia de patrones.  Es de solo lectura.  
  
## Sintaxis  
  
```  
  
RegExp.$n   
```  
  
## Parámetros  
 `RegExp`  
 Siempre es el objeto `RegExp` global.  
  
 `n`  
 Cualquier entero entre 1 y 9.  
  
## Comentarios  
 Los valores de las propiedades **$1...$9** se modifican cada vez que se obtiene una coincidencia correcta entre paréntesis.  En un patrón de expresión regular se puede especificar cualquier número de subcadenas entre paréntesis, pero solo se pueden almacenar las nueve más recientes.  
  
## Ejemplo  
 En el ejemplo siguiente se realiza una búsqueda de expresiones regulares.  Muestra coincidencias y subcoincidencias del objeto `RegExp` global.  Las subcoincidencias son coincidencias entre paréntesis correctas contenidas en las propiedades `$1…$9`.  En el ejemplo también se muestran coincidencias y subcoincidencias de la matriz devuelta por el método `exec`.  
  
```javascript  
var newLine = "<br />";  
  
var re = /(\w+)@(\w+)\.(\w+)/g  
var src = "Please send mail to george@contoso.com and someone@example.com. Thanks!"  
  
var result;  
var s = "";  
  
// Get the first match.  
result = re.exec(src);  
  
while (result != null) {  
    // Show the entire match.  
    s += newLine;  
  
    // Show the match and submatches from the RegExp global object.  
    s += "RegExp.lastMatch: " + RegExp.lastMatch + newLine;  
    s += "RegExp.$1: " + RegExp.$1 + newLine;  
    s += "RegExp.$2: " + RegExp.$2 + newLine;  
    s += "RegExp.$3: " + RegExp.$3 + newLine;  
  
    // Show the match and submatches from the array that is returned  
    // by the exec method.  
    for (var index = 0; index < result.length; index++) {  
        s +=  index + ": ";  
        s += result[index];  
        s += newLine;  
    }  
  
    // Get the next match.  
    result = re.exec(src);  
}  
document.write(s);  
  
// Output:  
//  RegExp.lastMatch: george@contoso.com  
//  RegExp.$1: george  
//  RegExp.$2: contoso  
//  RegExp.$3: com  
//  0: george@contoso.com  
//  1: george  
//  2: contoso  
//  3: com  
  
//  RegExp.lastMatch: someone@example.com  
//  RegExp.$1: someone  
//  RegExp.$2: example  
//  RegExp.$3: com  
//  0: someone@example.com  
//  1: someone  
//  2: example  
//  3: com  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [RegExp \(Objeto\)](../../javascript/reference/regexp-object-javascript.md)  
  
## Vea también  
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/es-es/ab0766e1-7037-45ed-aa23-706f58358c0e)