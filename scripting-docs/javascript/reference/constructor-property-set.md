---
title: "constructor (Propiedad, Set) | Microsoft Docs"
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
ms.assetid: f350b7eb-8994-40bf-9011-f8b20fcef34f
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# constructor (Propiedad, Set)
Especifica la función que crea un conjunto.  
  
## Sintaxis  
  
```javascript  
set.constructor  
```  
  
## Comentarios  
 El `set` necesario es el nombre del conjunto.  
  
 La propiedad `constructor` es miembro del prototipo de todos los objetos que tienen un prototipo.  Esto incluye todos los objetos intrínsecos de JavaScript excepto los objetos `Global` y `Math`.  La propiedad `constructor` contiene una referencia a la función que crea instancias de ese objeto concreto.  
  
## Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]