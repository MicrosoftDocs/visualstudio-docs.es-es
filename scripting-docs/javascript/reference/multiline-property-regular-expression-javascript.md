---
title: "multiline (Propiedad, Regular Expression de JavaScript) | Microsoft Docs"
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
  - "multiline"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "multiline (propiedad)"
ms.assetid: ca7b276a-1fe2-4189-ac27-f089ab3e9974
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# multiline (Propiedad, Regular Expression de JavaScript)
Devuelve un valor Boolean que indica el estado de la marca multiline \(**m**\) que se usa con una expresión regular.  El valor predeterminado es **false**.  Es de solo lectura.  
  
## Sintaxis  
  
```  
  
rgExp.multiline  
```  
  
## Comentarios  
 El argumento obligatorio `rgExp` es una instancia del objeto `RegExp`.  
  
 La propiedad **multiline** devuelve **true** si la marca multiline se establece para una expresión regular y **false** de lo contrario.  La propiedad **multiline** es **true** si el objeto de expresión regular se creó con la marca **m**.  
  
 Si el valor de **multiline** es **false**, "^" coincide con la posición del principio de una cadena y "$" coincide con la posición del final de una cadena.  Si el valor de **multiline** es **true**, "^" coincide con la posición del principio de una cadena y con la posición siguiente a "\\n" o "\\r", y "$" coincide con la posición del final de la cadena y con la posición anterior a "\\n" o "\\r".  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el comportamiento de la propiedad **multiline**.  Si pasas "m" a la función que se muestra a continuación, se reemplaza la palabra "while" con la palabra "and".  Esto se debe a que la marca multiline está establecida y la palabra "while" aparece al principio de la línea después de un carácter de nueva línea.  La marca multiline permite buscar en cadenas de varias líneas.  
  
```javascript  
function RegExpMultilineDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The man hit the ball with the bat ";  
   ss += "\nwhile the fielder caught the ball with the glove.";  
  
   // Replace "while" with "and".  
   var re = new RegExp("^while", flag);  
   var r = ss.replace(re, "and");          
  
   // Output the multiline flag and the resulting string.  
   var s = "";  
   s += "Result for multiline = " + re.multiline.toString();  
   s += ": " + r;  
  
   return(s);  
  
}  
  
sa = RegExpMultilineDemo("m");  
sb = RegExpMultilineDemo("");  
document.write (sa + "<br />" + sb);  
```  
  
## Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Se aplica a**: [Regular Expression \(Objeto\)](../../javascript/reference/regular-expression-object-javascript.md)  
  
## Vea también  
 [global \(Propiedad, Regular Expression\)](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [ignoreCase \(Propiedad, Regular Expression\)](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/es-es/ab0766e1-7037-45ed-aa23-706f58358c0e)