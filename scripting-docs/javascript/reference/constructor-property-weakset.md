---
title: "Propiedad constructor (WeakSet) | Microsoft Docs"
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
ms.assetid: 234e7104-9b78-4bfa-8f77-2bc44a570928
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Propiedad constructor (WeakSet)
Especifica la función que crea un `WeakSet`.  
  
## Sintaxis  
  
```javascript  
weakset.constructor  
```  
  
## Comentarios  
 El `weakset` requerido es el nombre del conjunto.  
  
 La propiedad `constructor` es un miembro del prototipo de cada objeto que tiene un prototipo.  Esto incluye todos los objetos intrínsecos de JavaScript, salvo los objetos `Global` y `Math`.  La propiedad `constructor` contiene una referencia a la función que crea instancias de ese objeto concreto.  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]