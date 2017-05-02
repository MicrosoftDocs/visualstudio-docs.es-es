---
title: "has (M&#233;todo, WeakMap de JavaScript) | Microsoft Docs"
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
ms.assetid: 12bedca1-bde7-413a-a4e2-06c03559044f
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# has (M&#233;todo, WeakMap de JavaScript)
Devuelve `true` si el objeto `WeakMap` contiene el elemento especificado.  
  
## Sintaxis  
  
```javascript  
weakmapObj.has(key)  
```  
  
#### Parámetros  
 `weakmapObj`  
 Requerido.  Un objeto `WeakMap`.  
  
 `key`  
 Requerido.  Clave del elemento que se va a probar.  
  
## Valor de propiedad y valor devuelto  
 `true` si `WeakMap` contiene la clave especificada.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo agregar un miembro a `WeakMap` y después utilizar `has` para comprobar si está presente.  
  
```javascript  
var dog = {  
    breed: "yorkie"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
  
document.write(wm.has(dog));  
  
// Output:  
// true  
```  
  
## Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]