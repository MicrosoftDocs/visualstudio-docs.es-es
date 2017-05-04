---
title: "prototype (Propiedad, WeakMap) | Microsoft Docs"
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
ms.assetid: d28b8a9b-38c9-443d-9586-7cc74784bd99
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# prototype (Propiedad, WeakMap)
Devuelve una referencia al prototipo para una objeto `WeakMap`.  
  
## Sintaxis  
  
```javascript  
weakmap.prototype  
```  
  
## Comentarios  
 El argumento `weakmap` es el nombre de un objeto `WeakMap`.  
  
 Utilice la propiedad `prototype` para proporcionar un conjunto base de funcionalidad a una clase de objetos.  Las nuevas instancias de un objeto "heredan" el comportamiento del prototipo asignado a ese objeto.  
  
 Por ejemplo, para agregar un método al objeto `WeakMap` que devuelve el valor del elemento mayor del `WeakMap`, declare la función, agréguela a `WeakMap.prototype` y después úsela.  
  
## Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]