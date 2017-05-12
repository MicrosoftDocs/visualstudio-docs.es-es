---
title: "Propiedad prototype (WeakSet) | Microsoft Docs"
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
ms.assetid: 950e15a2-2f56-4cb9-8e48-020efd97f938
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Propiedad prototype (WeakSet)
Devuelve una referencia al prototipo para una `WeakSet`.  
  
## Sintaxis  
  
```javascript  
weakset.prototype  
```  
  
## Comentarios  
 El argumento de `weakset` es el nombre de un conjunto.  
  
 Use la propiedad `prototype` para proporcionar un conjunto básico de funcionalidades a una clase de objetos.  Las nuevas instancias de un objeto «heredan» el comportamiento del prototipo asignado a dicho objeto.  
  
 Por ejemplo, para agregar un método al objeto `WeakSet` que devuelva el valor del elemento más grande del conjunto, declare la función, agréguela a `WeakSet.prototype` y, a continuación, úsela.  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]