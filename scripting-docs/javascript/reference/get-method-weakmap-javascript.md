---
title: "get (M&#233;todo, WeakMap de JavaScript) | Microsoft Docs"
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
ms.assetid: d922c55d-486d-4feb-aedc-1f4867c417d2
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# get (M&#233;todo, WeakMap de JavaScript)
Devuelve un elemento especificado de un objeto `WeakMap`.  
  
## Sintaxis  
  
```javascript  
weakmapObj.get(key)  
```  
  
#### Parámetros  
 `weakmapObj`  
 Requerido.  Un objeto `WeakMap`.  
  
 `key`  
 Requerido.  La clave de un elemento en `WeakMap`.  
  
## Valor de propiedad y valor devuelto  
 Devuelve el objeto asociado con la clave.  Si `WeakMap` no contiene la clave, este método devuelve un valor de `undefined`.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo recuperar miembros desde un objeto `WeakMap`.  
  
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
  
document.write(wm.get(dog) + ": ");  
document.write(dog.breed);  
document.write("<br />");  
document.write(wm.get(cat) + ": ");  
document.write(cat.breed);  
  
// Output:  
// fido: yorkie  
// pepper: burmese  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]