---
title: "constructor (Propiedad, Array) | Microsoft Docs"
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
ms.assetid: b78d517b-cb56-4866-b30f-ef8121a27843
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# constructor (Propiedad, Array)
Especifica la función que crea una matriz.  
  
## Sintaxis  
  
```  
  
array.constructor  
```  
  
## Comentarios  
 El argumento obligatorio `array` es el nombre de una matriz.  
  
 La propiedad `constructor` es un miembro del prototipo de todo objeto que tiene un prototipo.  Esto incluye todos los objetos intrínsecos de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] excepto los objetos `Global` y `Math`.  La propiedad `constructor` contiene una referencia a la función que crea instancias de ese objeto concreto.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso de la propiedad constructor.  
  
```javascript  
var x = new Array();  
  
if (x.constructor == Array)  
    document.write("Object is an Array.");  
else  
    document.write("Object is not an Array.");  
  
// Output:  
// Object is an Array.  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]