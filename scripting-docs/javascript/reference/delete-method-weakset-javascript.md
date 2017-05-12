---
title: "M&#233;todo delete (WeakSet) (JavaScript) | Microsoft Docs"
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
ms.assetid: 19e93366-7d42-4abf-b7b9-fcf943fa17a3
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# M&#233;todo delete (WeakSet) (JavaScript)
Elimina el elemento especificado de un `WeakSet`.  
  
## Sintaxis  
  
```javascript  
weaksetObj.delete(obj)  
```  
  
#### Parámetros  
 `weaksetObj`  
 Requerido.  Objeto `WeakSet`.  
  
 `obj`  
 Requerido.  Elemento que se va a quitar.  
  
## Valor de propiedad y valor devuelto  
 `true` si se ha eliminado el elemento.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra cómo agregar y eliminar elementos de un `WeakSet`.  
  
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