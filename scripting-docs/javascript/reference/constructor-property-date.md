---
title: "constructor (Propiedad, Date) | Microsoft Docs"
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
ms.assetid: 5db153a1-788b-4a61-bfc8-2d2ec38f36ea
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# constructor (Propiedad, Date)
Especifica la función que crea una fecha.  
  
## Sintaxis  
  
```  
  
date.constructor  
```  
  
## Comentarios  
 El parámetro obligatorio `date` es el nombre de un objeto de fecha.  
  
 La propiedad `constructor` es un miembro del prototipo de todo objeto que tiene un prototipo.  La propiedad `constructor` contiene una referencia a la función que crea instancias de ese objeto concreto.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso de la propiedad constructor.  
  
```javascript  
var x = new Date("Hi");  
  
if (x.constructor == Date)  
    document.write("Object is a date.");  
  
// Output:  
// Object is a date.  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]