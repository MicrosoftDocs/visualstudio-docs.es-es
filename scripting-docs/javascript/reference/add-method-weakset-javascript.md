---
title: "M&#233;todo add (WeakSet) (JavaScript) | Microsoft Docs"
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
ms.assetid: d35d0287-6b33-4720-b9d7-8954c428ce4e
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# M&#233;todo add (WeakSet) (JavaScript)
Agrega un nuevo elemento a un `WeakSet`.  
  
## Sintaxis  
  
```javascript  
weaksetObj.add(obj)  
```  
  
#### Parámetros  
 `weaksetObj`  
 Requerido.  Objeto `WeakSet`.  
  
 `obj`  
 Requerido.  Nuevo elemento del objeto `WeakSet`.  
  
## Comentarios  
 El nuevo elemento debe ser un objeto, y no un valor arbitrario, y además debe ser único.  Si agrega un elemento que no es único a `WeakSet`, el nuevo elemento no se agregará a la colección.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra cómo agregar miembros a un conjunto y verificar que se hayan agregado.  
  
```javascript  
var ws = new WeakSet();  
  
var str = new String("Thomas Jefferson");  
var num = new Number(1776);  
  
ws.add(str);  
ws.add(num);  
  
console.log(ws.has(str));  
console.log(ws.has(num));  
  
ws.delete(str);  
console.log(ws.has(str));  
  
// Output:  
// true  
// true  
// false  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]