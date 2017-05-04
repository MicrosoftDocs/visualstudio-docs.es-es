---
title: "length (Propiedad, Function de JavaScript) | Microsoft Docs"
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
  - "length (propiedad, function)"
ms.assetid: fdc8e1c9-0dac-4e1b-ba3a-11073c37ef63
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# length (Propiedad, Function de JavaScript)
Obtiene el número de argumentos definidos para una función.  
  
## Sintaxis  
  
```  
  
functionName.length  
```  
  
## Comentarios  
 El argumento obligatorio *functionName* es el nombre de la función.  
  
 El motor de scripting inicializa la propiedad **length** de una función con el número de argumentos establecido en su definición cuando se crea una instancia de la misma.  
  
 El resultado de llamar a una función con un número de argumentos distinto del valor de su propiedad **length** depende de la función.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso de la propiedad **length**:  
  
```javascript  
function ArgTest(a, b){  
    var s = "";  
  
    s += "Expected Arguments: " + ArgTest.length;  
    s += "<br />";  
    s += "Passed Arguments: " + arguments.length;  
  
    return s;  
}  
  
document.write(ArgTest(1, 2));  
  
// Output:   
// Expected Arguments: 2  
// Passed Arguments: 2  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## Vea también  
 [arguments \(Propiedad, Function\)](../../javascript/reference/arguments-property-function-javascript.md)   
 [length \(Propiedad, Array\)](../../javascript/reference/length-property-array-javascript.md)   
 [length \(Propiedad, String\)](../../javascript/reference/length-property-string-javascript.md)