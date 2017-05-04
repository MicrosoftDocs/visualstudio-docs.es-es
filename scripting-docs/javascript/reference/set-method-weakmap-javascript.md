---
title: "set (M&#233;todo, WeakMap de JavaScript) | Microsoft Docs"
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
ms.assetid: 29fc72b1-224f-4f19-8c06-5d926d695b03
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# set (M&#233;todo, WeakMap de JavaScript)
Agrega un nuevo elemento a un objeto `WeakMap`.  
  
## Sintaxis  
  
```javascript  
weakmapObj.set(key, value)  
```  
  
#### Parámetros  
 `weakmapObj`  
 Requerido.  Un objeto `WeakMap`.  
  
 `key`  
 Requerido.  Objeto que representa la clave del elemento que se va a agregar.  Debe ser una referencia de objeto.  
  
 `value`  
 Requerido.  Valor del elemento que se va a agregar.  
  
## Valor de propiedad y valor devuelto  
 Devuelve el objeto `WeakMap` que contiene los nuevos pares clave\-valor.  
  
## Comentarios  
 Si agrega un valor a la colección utilizando una clave existente, el nuevo valor reemplazará el valor antiguo.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra la forma de agregar miembros a un objeto `WeakMap`.  
  
```javascript  
var dog = {  
    breed: "yorkie"  
}  
  
var cat = {  
    breed: "burmese"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.set(cat, "pepper");  
```  
  
## Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]