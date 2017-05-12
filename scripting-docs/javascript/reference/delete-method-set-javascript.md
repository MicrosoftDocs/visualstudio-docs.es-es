---
title: "delete (M&#233;todo, Set de JavaScript) | Microsoft Docs"
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
ms.assetid: 052c409e-10c9-49f2-955d-5ad7e31c14f3
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# delete (M&#233;todo, Set de JavaScript)
Quita el elemento especificado de un conjunto.  
  
## Sintaxis  
  
```javascript  
setObj.delete(value)  
```  
  
#### Parámetros  
 `setObj`  
 Requerido.  Un objeto `Set`.  
  
 `value`  
 Requerido.  Elemento que se va a quitar.  
  
## Valor de propiedad y valor devuelto  
 `true` si el elemento ya se ha quitado.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo agregar miembros a `Set` y después eliminar uno de ellos.  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
s.delete("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776,  
```  
  
## Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]