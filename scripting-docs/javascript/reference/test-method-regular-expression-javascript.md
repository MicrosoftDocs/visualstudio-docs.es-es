---
title: "test (M&#233;todo, Regular Expression de JavaScript) | Microsoft Docs"
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
  - "test"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "método de prueba"
ms.assetid: 4f4b6e39-cb1a-4be9-a66f-7b846075580d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# test (M&#233;todo, Regular Expression de JavaScript)
Devuelve un valor Boolean que indica si existe o no un patrón en una cadena de búsqueda.  
  
## Sintaxis  
  
```  
  
rgExp.test(str)   
```  
  
## Parámetros  
 `rgExp`  
 Obligatorio.  Instancia de un objeto **Regular Expression** que contiene el patrón de expresión regular y las marcas aplicables.  
  
 `str`  
 Obligatorio.  Cadena en la que se va a buscar.  
  
## Comentarios  
 El método **test** comprueba si existe un patrón dentro de una cadena: devuelve **true** si existe y **false** de lo contrario.  
  
 El método **test** no modifica las propiedades del objeto `RegExp` global.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método **test**.  Para usar este ejemplo, pase a la función un patrón de expresión regular y una cadena.  La función busca la presencia del patrón de expresión regular en la cadena y devuelve una cadena que indica el resultado de la búsqueda:  
  
```javascript  
function TestDemo(re, teststring)  
{  
   // Test string for existence of regular expression.  
   var found = re.test(teststring)  
  
   // Format the output.  
   var s = "";  
   s += "'" + teststring + "'"  
  
   if (found)  
      s += " contains ";  
   else  
      s += " does not contain ";  
  
   s += "'" + re.source + "'"  
   return(s);  
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Regular Expression \(Objeto\)](../../javascript/reference/regular-expression-object-javascript.md)  
  
## Vea también  
 [RegExp \(Objeto\)](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression \(Objeto\)](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/es-es/ab0766e1-7037-45ed-aa23-706f58358c0e)