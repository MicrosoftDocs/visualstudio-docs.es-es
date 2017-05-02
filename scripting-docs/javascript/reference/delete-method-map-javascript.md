---
title: "delete (M&#233;todo, Map de JavaScript) | Microsoft Docs"
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
ms.assetid: a073e1a1-5862-485b-b2bd-26c66a3aff51
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# delete (M&#233;todo, Map de JavaScript)
Quita el elemento especificado de un mapa.  
  
## Sintaxis  
  
```javascript  
mapObj.delete(key)  
```  
  
#### Parámetros  
 `mapObj`  
 Requerido.  Un objeto `Map`.  
  
 `key`  
 Requerido.  Clave del elemento que se va a quitar.  
  
## Valor de propiedad y valor devuelto  
 `true` si el elemento ya se ha quitado.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo agregar miembros a `Map` y después eliminar uno de ellos.  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.delete(1);  
  
m.forEach(function (item) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// red  
// 2  
```  
  
## Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]