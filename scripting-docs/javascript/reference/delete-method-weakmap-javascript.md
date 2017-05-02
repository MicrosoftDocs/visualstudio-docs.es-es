---
title: "delete (M&#233;todo, WeakMap de JavaScript) | Microsoft Docs"
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
ms.assetid: 7d54ae55-e514-45ba-b403-d1eee46837d2
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# delete (M&#233;todo, WeakMap de JavaScript)
Quita el elemento especificado de un objeto `WeakMap`.  
  
## Sintaxis  
  
```javascript  
weakmapObj.delete(key)  
```  
  
#### Parámetros  
 `weakmapObj`  
 Requerido.  Un objeto `WeakMap`.  
  
 `key`  
 Requerido.  Clave del elemento que se va a quitar.  
  
## Valor de propiedad y valor devuelto  
 `true` si el elemento ya se ha quitado.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo agregar un miembro a `WeakMap` y después eliminarlo.  
  
```javascript  
function Dog(breed) {  
    this.breed = breed;  
}  
  
var dog = new Dog("yorkie");  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.delete(dog);  
```  
  
## Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]