---
title: "constructor (Propiedad, Number) | Microsoft Docs"
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
ms.assetid: a348fe53-1b4a-42f5-964b-53d57342c906
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# constructor (Propiedad, Number)
Especifica la función que crea un objeto Number.  
  
## Sintaxis  
  
```  
  
number.constructor  
```  
  
## Comentarios  
 El argumento obligatorio `number` es el nombre de una cadena.  
  
 La propiedad `constructor` es un miembro del prototipo de todo objeto que tiene un prototipo.  Esto incluye todos los objetos intrínsecos de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] excepto los objetos `Global` y `Math`.  La propiedad `constructor` contiene una referencia a la función que crea instancias de ese objeto concreto.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso de la propiedad constructor.  
  
```javascript  
var num = new Number();  
  
if (num.constructor == Number)  
    document.write("Object is a Number.");  
else  
    document.write("Object is not a Number.");  
  
// Output:  
// Object is a Number.  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]