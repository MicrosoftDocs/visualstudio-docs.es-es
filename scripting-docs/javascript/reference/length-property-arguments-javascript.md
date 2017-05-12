---
title: "length (Propiedad, argumentos de JavaScript) | Microsoft Docs"
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
  - "length Property"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Length (propiedad)"
  - "length (propiedad, arguments)"
ms.assetid: 3cf36823-15bc-489b-a951-24c4923d9dba
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# length (Propiedad, argumentos de JavaScript)
Devuelve el número real de argumentos que el llamador pasa a una función.  
  
## Sintaxis  
  
```  
[function.]arguments.length  
```  
  
## Comentarios  
 El argumento opcional *function* es el nombre del objeto `Function` que se está ejecutando actualmente.  
  
 El motor de scripting inicializa la propiedad **length** del objeto **arguments** con el número real de argumentos pasados a un objeto `Function` cuando comienza la ejecución de esa función.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso de la propiedad **length** del objeto **arguments**.  Para comprender totalmente el ejemplo, pasa más argumentos a la función que los 2 argumentos esperados:  
  
```javascript  
function ArgTest(a, b){  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
  
   document.write (s);  
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Se aplica a**: [arguments \(Objeto\)](../../javascript/reference/arguments-object-javascript.md)&#124; [Function \(Objeto\)](../../javascript/reference/function-object-javascript.md)  
  
## Vea también  
 [arguments \(Propiedad, Function\)](../../javascript/reference/arguments-property-function-javascript.md)   
 [length \(Propiedad, Array\)](../../javascript/reference/length-property-array-javascript.md)   
 [length \(Propiedad, String\)](../../javascript/reference/length-property-string-javascript.md)