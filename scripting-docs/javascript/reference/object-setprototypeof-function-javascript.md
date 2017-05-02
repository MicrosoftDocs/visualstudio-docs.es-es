---
title: "Object.getPrototypeOf (funci&#243;n de JavaScript) | Microsoft Docs"
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
ms.assetid: a2609f6e-aeee-4c13-b7cf-c31ddf58ff35
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Object.getPrototypeOf (funci&#243;n de JavaScript)
Establece el prototipo de un objeto.  
  
## Sintaxis  
  
```  
Object.setPrototypeOf(obj, proto);  
```  
  
#### Parámetros  
 `obj`  
 Requerido.  El objeto para el que va a establecer el prototipo.  
  
 `proto`  
 Requerido.  El nuevo objeto prototipo.  
  
## Comentarios  
  
> [!WARNING]
>  Establecer el prototipo puede reducir el rendimiento de todo el código JavaScript con acceso a un objeto cuyo prototipo ha mutado.  
  
## Ejemplo  
 En el ejemplo de código siguiente se muestra cómo establecer el prototipo de un objeto.  
  
```javascript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
if (console && console.log) {  
    console.log(Object.getPrototypeOf(rec) === Rectangle.prototype);  // Returns true  
    Object.getPrototypeOf(rec, Object.prototype);  
    console.log(Object.getPrototypeOf(rec) === Rectangle.prototype);  // Returns false  
}  
```  
  
## Ejemplo  
 En el ejemplo de código siguiente se muestra cómo agregar propiedades a un objeto agregándolas al prototipo.  
  
```javascript  
var proto = { y: 2 };  
  
var obj = { x: 10 };  
Object.getPrototypeOf(obj, proto);  
  
proto.y = 20;  
proto.z = 40;  
  
if (console && console.log) {  
    console.log(obj.x === 10);  // Returns true  
    console.log(obj.y === 20);  // Returns true  
    console.log(obj.z === 40);  // Returns true  
}  
```  
  
## Ejemplo  
 En el ejemplo de código siguiente se agregan propiedades al objeto `String` estableciendo un nuevo prototipo en él.  
  
```javascript  
var stringProp = { desc: "description" };  
  
Object.getPrototypeOf(String, stringProp);  
var s1 = "333";  
var s2 = new String("333");  
  
if (console && console.log) {  
  
    console.log(String.desc === "description"); // Returns true  
    console.log(s1.desc === "description");     // Returns false  
    console.log(s2.desc === "description");     // Returns false  
  
    Object.getPrototypeOf(s1, String); // Can't be set.  
    Object.getPrototypeOf(s2, String);  
  
    console.log(s1.desc === "description"); // Returns false  
    console.log(s2.desc === "description"); // Returns true  
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]