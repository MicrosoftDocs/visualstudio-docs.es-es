---
title: "lastIndex (Propiedad, RegExp de JavaScript) | Microsoft Docs"
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
  - "lastIndex"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "lastIndex (propiedad)"
ms.assetid: c8ae2a13-6dff-4cbe-b662-aca3d66c2a7f
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# lastIndex (Propiedad, RegExp de JavaScript)
Devuelve la posición del carácter donde comienza la siguiente coincidencia en una cadena de búsqueda.  
  
## Sintaxis  
  
```  
  
RegExp.lastIndex  
```  
  
## Comentarios  
 El objeto asociado con esta propiedad siempre es el objeto `RegExp` global.  
  
 La propiedad `lastIndex` está basada en cero; es decir, el índice del primer carácter es cero.  Su valor inicial es –1.  Su valor cambia cada vez que se produce una coincidencia correcta.  
  
 Los métodos `exec` y **test** del objeto `RegExp`, y los métodos `match`, **replace** y **split** del objeto `String` modifican la propiedad `lastIndex`.  
  
 Las siguientes reglas se aplican a los valores de `lastIndex`:  
  
-   Si no hay ninguna coincidencia, `lastIndex` se establece en \-1.  
  
-   Si `lastIndex` es mayor que la longitud de la cadena, los métodos **test** y `exec` dan un error y `lastIndex` se establece en \-1.  
  
-   Si `lastIndex` es igual a la longitud de la cadena, la expresión regular coincide si el modelo coincide con la cadena vacía.  De lo contrario, la coincidencia produce un error y `lastIndex` se restablece en \-1.  
  
-   De lo contrario, `lastIndex` se establece en la siguiente posición a continuación de la coincidencia más reciente.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso de la propiedad `lastIndex`.  Esta función recorre en iteración una cadena de búsqueda e imprime los valores de **index** y `lastIndex` para cada palabra de la cadena.  
  
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
      document.write (arr.index + "-" + re.lastIndex + " ");  
      document.write (arr);  
      }  
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [RegExp \(Objeto\)](../../javascript/reference/regexp-object-javascript.md)  
  
## Vea también  
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/es-es/ab0766e1-7037-45ed-aa23-706f58358c0e)