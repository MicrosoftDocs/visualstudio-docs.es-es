---
title: "prototype (Propiedad, Set) | Microsoft Docs"
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
ms.assetid: a075d5a6-e502-4636-85fc-1af001b8ac35
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# prototype (Propiedad, Set)
Devuelve una referencia al prototipo para un conjunto.  
  
## Sintaxis  
  
```javascript  
set.prototype  
```  
  
## Comentarios  
 El argumento `set` es el nombre de un conjunto.  
  
 Utilice la propiedad `prototype` para proporcionar un conjunto base de funcionalidad a una clase de objetos.  Las nuevas instancias de un objeto "heredan" el comportamiento del prototipo asignado a ese objeto.  
  
 Por ejemplo, para agregar un método al objeto `Set` que devuelve el valor del elemento mayor del conjunto, declare la función, agréguela a `Set.prototype` y después úsela.  
  
## Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]