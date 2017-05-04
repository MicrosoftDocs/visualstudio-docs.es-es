---
title: "set (M&#233;todo, Map de JavaScript) | Microsoft Docs"
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
ms.assetid: 31ee71a0-b09d-442a-9e02-825accf94ffa
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# set (M&#233;todo, Map de JavaScript)
Agrega un nuevo elemento a un mapa.  
  
## Sintaxis  
  
```javascript  
mapObj.set(key, value)  
```  
  
#### Parámetros  
 `mapObj`  
 Requerido.  Un objeto `Map`.  
  
 `key`  
 Requerido.  Clave del nuevo elemento.  
  
 `value`  
 Requerido.  Valor del elemento que se va a agregar.  
  
## Valor de propiedad y valor devuelto  
 Devuelve el objeto `Map` que contiene los nuevos pares clave\-valor.  
  
## Comentarios  
 Si agrega un valor a la colección utilizando una clave existente, el nuevo valor reemplazará el valor antiguo.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo agregar miembros a `Map` y después recuperarlos.  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
m.forEach(function (item) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// black  
// red  
// 2  
```  
  
## Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]