---
title: "M&#233;todo has (WeakSet) (JavaScript) | Microsoft Docs"
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
ms.assetid: e24f0876-26bd-4007-b12a-360bb6fa0951
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# M&#233;todo has (WeakSet) (JavaScript)
Devuelve `true` si `WeakSet` contiene el elemento especificado.  
  
## Sintaxis  
  
```javascript  
setObj.has(obj)  
```  
  
#### Parámetros  
 `setObj`  
 Requerido.  Objeto `WeakSet`.  
  
 `obj`  
 Requerido.  Elemento que se va a comprobar.  
  
## Valor de propiedad y valor devuelto  
 `true` si el conjunto contiene el elemento especificado.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo agregar miembros a un `WeakSet` y, a continuación, comprobar si el conjunto contiene un miembro específico.  
  
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