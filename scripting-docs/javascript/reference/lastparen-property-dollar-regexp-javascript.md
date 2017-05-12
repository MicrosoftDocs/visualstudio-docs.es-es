---
title: "lastParen (Propiedad) ($+) (RegExp) (JavaScript) | Microsoft Docs"
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
  - "$+"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "lastParen (propiedad) ($+)"
ms.assetid: 18aca591-a97a-48da-8b06-422346804b16
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# lastParen (Propiedad) ($+) (RegExp) (JavaScript)
Devuelve la última subcoincidencia entre paréntesis de una búsqueda de expresiones regulares, si la hubiera.  Es de solo lectura.  
  
## Sintaxis  
  
```  
  
RegExp.lastParen  
```  
  
## Comentarios  
 El objeto asociado con esta propiedad siempre es el objeto `RegExp` global.  
  
 El valor inicial de la propiedad `lastParen` es una cadena vacía.  El valor de la propiedad `lastParen` cambia cada vez que se obtiene una coincidencia correcta.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso de la propiedad `lastParen`:  
  
```javascript  
// Create the regular expression pattern.  
var re = new RegExp("d(b+)(d)","ig");  
var str = "cdbBdbsbdbdz";  
  
// Perform the search.  
var arr = re.exec(str);  
  
// Print the output.  
var s = ""   
s += "$1: " + RegExp.$1 + "<br />";  
s += "$2: " + RegExp.$2 + "<br />";  
s += "$3: " + RegExp.$3 + "<br />";  
s += "input: " + RegExp.input + "<br />";  
s += "lastMatch: " + RegExp.lastMatch + "<br />";  
s += "leftContext: " + RegExp.leftContext + "<br />";  
s += "rightContext: " + RegExp.rightContext + "<br />";   
s += "lastParen: " + RegExp.lastParen + "<br />";  
  
document.write(s);  
```  
  
## Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Se aplica a**: [RegExp \(Objeto\)](../../javascript/reference/regexp-object-javascript.md)  
  
## Vea también  
 [$1...$9 \(Propiedades, RegExp\)](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md)   
 [index \(Propiedad, RegExp\)](../../javascript/reference/index-property-regexp-javascript.md)   
 [input \(Propiedad\) \($\_\) \(RegExp\)](../../javascript/reference/input-property-dollar-regexp-javascript.md)   
 [lastIndex \(Propiedad, RegExp\)](../../javascript/reference/lastindex-property-regexp-javascript.md)   
 [lastMatch \(Propiedad\) \($&\) \(RegExp\)](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md)   
 [leftContext \(Propiedad\) \($\`\) \(RegExp\)](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md)   
 [rightContext \(Propiedad\) \($'\) \(RegExp\)](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)