---
title: "global (Propiedad, Regular Expression, JavaScript) | Microsoft Docs"
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
  - "Global"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "global (propiedad)"
ms.assetid: 76a0f115-0d89-4aca-86d5-932895c6d649
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# global (Propiedad, Regular Expression, JavaScript)
Devuelve un valor Boolean que indica el estado de la marca global \(**g**\) usada con una expresión regular.  El valor predeterminado es **false**.  Es de solo lectura.  
  
## Sintaxis  
  
```  
  
rgExp.global  
```  
  
## Comentarios  
 La referencia obligatoria `rgExp` es una instancia de un objeto **Regular Expression**.  
  
 La propiedad `global` devuelve **true** si la marca global se establece para una expresión regular y **False** de lo contrario.  
  
 Cuando se usa, la marca global indica que en una búsqueda se deben buscar todas las repeticiones del patrón dentro de la cadena de búsqueda y no solo la primera.  También se conoce como coincidencia global.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso de la propiedad `global`.  Si pasas **g** a la función que se muestra más abajo, todas las instancias de la palabra "the" se reemplazan con la palabra "a".  Observa que la palabra "The" situada al principio de la cadena no se reemplaza porque la marca **i** \(omitir mayúsculas y minúsculas\) no se pasa a la función.  
  
 Esta función muestra la condición de las propiedades asociadas a las marcas permitidas de expresiones regulares, que son **g**, **i** y **m**.  La función también muestra la cadena una vez realizados todos los reemplazos.  
  
```javascript  
function RegExpPropDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The batter hit the ball with the bat ";  
   ss += "and the fielder caught the ball with the glove.";  
  
   //Replace "the" with "a".  
   var re = new RegExp("the", flag);  
   var r = ss.replace(re, "a");          
  
   // Output the resulting string and the flags.  
   var s = "";  
   s += "global: " + re.global.toString();  
   s += "<br />";  
   s += "ignoreCase: " + re.ignoreCase.toString();  
   s += "<br />";  
   s += "multiline: " + re.multiline.toString();  
   s += "<br />";  
   s += "Resulting String: " + r;  
  
   return (s);  
}  
  
document.write(RegExpPropDemo("g"));  
```  
  
## Ejemplo  
 A continuación se muestra el resultado que se obtiene.  
  
```javascript  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Se aplica a**: [Regular Expression \(Objeto\)](../../javascript/reference/regular-expression-object-javascript.md)  
  
## Vea también  
 [ignoreCase \(Propiedad, Regular Expression\)](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [multiline \(Propiedad, Regular Expression\)](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/es-es/ab0766e1-7037-45ed-aa23-706f58358c0e)