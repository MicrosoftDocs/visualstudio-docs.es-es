---
title: "__proto__ (Propiedad, Objeto de JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__proto__"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 97c3f84d-125e-4905-b921-b021264964ee
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# __proto__ (Propiedad, Objeto de JavaScript)
Contiene una referencia al prototipo interno del objeto especificado.  
  
## Sintaxis  
  
```  
object.__proto__  
```  
  
#### Parámetros  
 `object`  
 Requerido.  Objeto en el que se va a establecer el prototipo.  
  
## Comentarios  
 La propiedad `__proto__` se puede utilizar para establecer el prototipo de un objeto.  
  
 El objeto o la función hereda todos los métodos y propiedades del nuevo prototipo, junto con todos los métodos y propiedades de la cadena de prototipo del nuevo prototipo.  Un objeto puede tener un solo prototipo \(sin incluir prototipos heredados en la cadena prototipo\), así que cuando llama a la propiedad `__proto__`, se reemplaza el prototipo anterior.  
  
 Puede establecer el prototipo solo en un objeto extensible.  Para obtener más información, vea [Object.preventExtensions \(Función\)](../../javascript/reference/object-preventextensions-function-javascript.md).  
  
> [!NOTE]
>  El nombre de propiedad `__proto__` comienza y finaliza con dos subrayados.  
  
## Ejemplo  
 En el ejemplo de código siguiente se muestra cómo se establece el prototipo de un objeto.  
  
```javascript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
if (console && console.log) {  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns true  
    rec.__proto__ = Object.prototype;  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns false  
}  
```  
  
## Ejemplo  
 El ejemplo de código siguiente muestra cómo agregar propiedades a un objeto al agregarlas al prototipo.  
  
```javascript  
var proto = { y: 2 };  
  
var obj = { x: 10 };  
obj.__proto__ = proto;  
  
proto.y = 20;  
proto.z = 40;  
  
if (console && console.log) {  
    console.log(obj.x === 10);  // Returns true  
    console.log(obj.y === 20);  // Returns true  
    console.log(obj.z === 40);  // Returns true  
}  
```  
  
## Ejemplo  
 El siguiente ejemplo de código agrega propiedades al objeto `String` estableciendo un nuevo prototipo en él.  
  
```javascript  
var stringProp = { desc: "description" };  
  
String.__proto__ = stringProp;  
var s1 = "333";  
var s2 = new String("333");  
  
if (console && console.log) {  
  
    console.log(String.desc === "description"); // Returns true  
    console.log(s1.desc === "description");     // Returns false  
    console.log(s2.desc === "description");     // Returns false  
  
    s1.__proto__ = String;  // Can't be set.  
    s2.__proto__ = String;  
  
    console.log(s1.desc === "description"); // Returns false  
    console.log(s2.desc === "description"); // Returns true  
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Vea también  
 [Prototipos y herencia de prototipo](../../javascript/advanced/prototypes-and-prototype-inheritance.md)