---
title: "ignoreCase (Propiedad, Regular Expression de JavaScript) | Microsoft Docs"
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
  - "ignoreCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "IgnoreCase (propiedad)"
ms.assetid: 816f0df5-5a82-44a5-a4ab-dbc91fa76e61
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# ignoreCase (Propiedad, Regular Expression de JavaScript)
Devuelve un valor Boolean que indica el estado de la marca ignoreCase \(**i**\) que se usa con una expresión regular.  El valor predeterminado es **false**.  Es de solo lectura.  
  
## Sintaxis  
  
```  
  
rgExp.ignoreCase  
```  
  
## Comentarios  
 La referencia obligatoria `rgExp` es una instancia del objeto `RegExp`.  
  
 La propiedad **ignoreCase** devuelve **true** si la marca ignoreCase se establece para una expresión regular y **false** de lo contrario.  
  
 Cuando se usa, la marca ignoreCase indica que una búsqueda debe pasar por alto la distinción entre mayúsculas y minúsculas al buscar el patrón incluido en la cadena de búsqueda.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso de la propiedad **ignoreCase**.  Si pasas "gi" a la función que se muestra más abajo, todas las instancias de la palabra "the" se reemplazan con la palabra "a", incluida la instancia inicial "The".  Esto se debe a que cuando está establecida la marca ignoreCase, la búsqueda no distingue mayúsculas de minúsculas.  Por tanto, en la búsqueda de coincidencias se considera que "T" es igual que "t".  
  
 Esta función devuelve valores Boolean que indican el estado de las marcas de expresión regular permitidas, que son **g**, **i** y **m**.  La función también devuelve la cadena resultante después de realizar todos los reemplazos.  
  
```javascript  
function RegExpPropDemo(flag){  
    // The flag parameter is a string that contains  
    // g, i, or m. The flags can be combined.  
  
    // Check flags for validity.  
    if (flag.match(/[^gim]/))  
        {  
        return ("Flag specified is not valid");  
        }  
  
    // Create the string on which to perform the replacement.  
    var orig = "The batter hit the ball with the bat ";  
    orig += "and the fielder caught the ball with the glove.";  
  
    // Replace "the" with "a".  
    var re = new RegExp("the", flag);  
    var r = orig.replace(re, "a");          
  
    // Output the resulting string and the values of the flags.  
    var s = "";  
    s += "global: " + re.global.toString();  
    s += "<br />";  
    s += "ignoreCase: " + re.ignoreCase.toString();  
    s += "<br />";  
    s += "multiline: " + re.multiline.toString();  
    s += "<br />";  
    s += "Resulting String: " + r;  
    s += "<br />";  
    s += "<br />";  
    return (s);  
}  
  
document.write(RegExpPropDemo("gi"));  
document.write(RegExpPropDemo("g"));  
```  
  
## Ejemplo  
 A continuación se muestra el resultado que se obtiene.  
  
```javascript  
global: true  
ignoreCase: true  
multiline: false  
Resulting String: a batter hit a ball with a bat and a fielder caught a ball with a glove.  
  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Se aplica a**: [Regular Expression \(Objeto\)](../../javascript/reference/regular-expression-object-javascript.md)  
  
## Vea también  
 [global \(Propiedad, Regular Expression\)](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [multiline \(Propiedad, Regular Expression\)](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/es-es/ab0766e1-7037-45ed-aa23-706f58358c0e)