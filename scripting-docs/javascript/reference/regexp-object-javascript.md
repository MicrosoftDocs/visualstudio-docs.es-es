---
title: "RegExp (Objeto de JavaScript) | Microsoft Docs"
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
  - "RegExp"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "RegExp (objeto)"
  - "RegExp (objeto), información general"
ms.assetid: 7f6b1073-8cbb-49ed-94b6-56833ba663c5
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# RegExp (Objeto de JavaScript)
Objeto intrínseco global que almacena información sobre los resultados de las coincidencias del patrón de expresión regular.  
  
## Sintaxis  
  
```  
  
RegExp.property   
```  
  
## Comentarios  
 El argumento obligatorio *property* puede ser cualquiera de las propiedades del objeto `RegExp`.  
  
 El objeto `RegExp` no se puede crear directamente, pero siempre está disponible para su uso.  Hasta que se completa correctamente una búsqueda de expresión regular, los valores iniciales de las diversas propiedades del objeto `RegExp` son las siguientes:  
  
|Propiedad|Forma abreviada|Valor inicial|  
|---------------|---------------------|-------------------|  
|index||\-1|  
|input|$\_|Cadena vacía.|  
|lastIndex||\-1|  
|lastMatch|$&|Cadena vacía.|  
|lastParen|$\+|Cadena vacía.|  
|leftContext|$\`|Cadena vacía.|  
|rightContext|$'|Cadena vacía.|  
|$1 \- $9|$1 \- $9|Cadena vacía.|  
  
 Sus propiedades tienen un valor no definido hasta que se completa una búsqueda correcta de expresión regular.  
  
 No se debe confundir el objeto global `RegExp` con el objeto **Regular Expression**.  Aunque parecen lo mismo, son independientes y distintos.  Las propiedades del objeto global `RegExp` contienen información actualizada continuamente sobre cada coincidencia a medida que tiene lugar, mientras que las propiedades del objeto **Regular Expression** solo contienen información sobre las coincidencias que tienen lugar dentro de esa instancia de la expresión regular **Regular Expression**.  
  
## Ejemplo  
 En el ejemplo siguiente se realiza una búsqueda de expresiones regulares.  Se muestran las coincidencias y subcoincidencias del objeto `RegExp` global y de la matriz devuelta por el método `exec`.  
  
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
  
<a name="js56jsobjregexpprop"></a>   
## Propiedades  
 [$1...$9 \(Propiedades\)](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md) &#124; [index \(Propiedad\)](../../javascript/reference/index-property-regexp-javascript.md) &#124; [input \(Propiedad\)](../../javascript/reference/input-property-dollar-regexp-javascript.md) &#124; [lastIndex \(Propiedad\)](../../javascript/reference/lastindex-property-regexp-javascript.md) &#124; [lastMatch \(Propiedad\)](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md) &#124; [lastParen \(Propiedad\)](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md) &#124; [leftContext \(Propiedad\)](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md) &#124; [rightContext \(Propiedad\)](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)  
  
## Métodos  
 El objeto `RegExp` no tiene métodos.  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Vea también  
 [Regular Expression \(Objeto\)](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/es-es/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [String \(Objeto\)](../../javascript/reference/string-object-javascript.md)