---
title: "constructor (Propiedad, String) | Microsoft Docs"
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
ms.assetid: ef0e9c82-4651-4404-87b1-d00cad38c6f9
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# constructor (Propiedad, String)
Especifica la función que crea una cadena.  
  
## Sintaxis  
  
```  
  
string.constructor  
```  
  
## Comentarios  
 El argumento obligatorio `string` es el nombre de una cadena.  
  
 La propiedad `constructor` es un miembro del prototipo de todo objeto que tiene un prototipo.  Esto incluye todos los objetos intrínsecos de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] excepto los objetos `Global` y `Math`.  La propiedad `constructor` contiene una referencia a la función que crea instancias de ese objeto concreto.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso de la propiedad constructor.  
  
```javascript  
var x = new String();  
  
if (x.constructor == String)  
    document.write("Object is a String.");  
else  
    document.write("Object is not a String.");  
  
// Output:  
// Object is a String.  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]