---
title: "add (M&#233;todo, Set de JavaScript) | Microsoft Docs"
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
ms.assetid: b4eea447-fd5b-4380-978e-1b95f6dbc438
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# add (M&#233;todo, Set de JavaScript)
Agrega un nuevo elemento a un conjunto.  
  
## Sintaxis  
  
```javascript  
setObj.add(value)  
```  
  
#### Parámetros  
 `setObj`  
 Requerido.  Un objeto `Set`.  
  
 `value`  
 Requerido.  Nuevo elemento del objeto `Set`.  
  
## Comentarios  
 El nuevo elemento puede ser de cualquier tipo y debe ser único.  Si agrega un elemento que no es único a `Set`, el nuevo elemento no se agregará a la colección.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo agregar miembros a set y después recuperarlos.  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]