---
title: "prototype (Propiedad, Map) | Microsoft Docs"
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
ms.assetid: c7b429cb-97b7-400e-a214-1b18bddd6b02
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# prototype (Propiedad, Map)
Devuelve una referencia al prototipo para un mapa.  
  
## Sintaxis  
  
```javascript  
map.prototype  
```  
  
## Comentarios  
 El argumento `map` es el nombre de una asignación.  
  
 Utilice la propiedad `prototype` para proporcionar un conjunto base de funcionalidad a una clase de objetos.  Las nuevas instancias de un objeto "heredan" el comportamiento del prototipo asignado a ese objeto.  
  
 Por ejemplo, para agregar un método al objeto `Map` que devuelve el valor del elemento mayor del conjunto, declare la función, agréguela a `Map.prototype` y después úsela.  
  
## Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]