---
title: "constructor (Propiedad, Error) | Microsoft Docs"
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
ms.assetid: 18aea278-2bd5-457b-83a5-d8d8f1226e0c
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# constructor (Propiedad, Error)
Especifica la función que crea un error.  
  
## Sintaxis  
  
```  
  
error.constructor  
```  
  
## Comentarios  
 El parámetro obligatorio `error` es el nombre de un objeto de error.  
  
 La propiedad `constructor` es un miembro del prototipo de todo objeto que tiene un prototipo.  La propiedad `constructor` contiene una referencia a la función que crea instancias de ese objeto concreto.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso de la propiedad constructor.  
  
```javascript  
var x = new Error("This is an error");  
  
if (x.constructor == Error)  
    document.write("Object is an error.");  
  
// Output:  
// Object is an error.  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]