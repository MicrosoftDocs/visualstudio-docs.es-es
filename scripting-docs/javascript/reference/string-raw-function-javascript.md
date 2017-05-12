---
title: "Funci&#243;n String.raw (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: b1038b73-3944-4645-b075-3a674b313762
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Funci&#243;n String.raw (JavaScript)
Devuelve la forma de cadena sin formato de una cadena de plantilla.  
  
## Sintaxis  
  
```  
String.raw`templateStr`;  
String.raw(obj, ...substitutions);  
```  
  
#### Parámetros  
 `templateStr`  
 Requerido.  Cadena de la plantilla.  
  
 `obj`  
 Requerido.  Un objeto formado correctamente especificado mediante la notación literal de objeto, como {raw: 'valor'}.  
  
 `...substitutions`  
 Opcional.  Una matriz \(un [parámetro rest](../../javascript/functions-javascript.md)\) que consta de uno o más valores de sustitución.  
  
## Comentarios  
 La función `String.raw` está pensada para usarse con [cadenas de plantillas](../../javascript/advanced/template-strings-javascript.md).  La cadena sin formato incluirá todos los caracteres de escape y barras diagonales inversas que se encuentren en la cadena.  
  
 Se produce un error si `obj` no es un objeto bien formado.  
  
## Ejemplo  
  
```  
function log(arg) {  
    if(console && console.log) {  
        console.log(arg);  
    }  
};  
  
var name = "bob";  
  
log(`hello \t${name}`);  
log(String.raw`hello \t${name}`);  
// The following usage for String.raw is supported but  
// is not typical.  
log(String.raw({ raw: 'fred'}, 'F', 'R', 'E'));  
  
// Output:  
// hello   bob  
// hello \tbob  
// fFrReEd  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]