---
title: "Object.getPrototypeOf (Funci&#243;n de JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "getPrototypeOf (función) [JavaScript]"
  - "Object.getPrototypeOf (función) [JavaScript]"
ms.assetid: 1c59cd7a-a7e2-4c5c-83ec-e6bd2b104d9f
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Object.getPrototypeOf (Funci&#243;n de JavaScript)
Devuelve el prototipo de un objeto.  
  
## Sintaxis  
  
```javascript  
Object.getPrototypeOf(object)  
```  
  
#### Parámetros  
 `object`  
 Obligatorio.  Objeto que hace referencia al prototipo.  
  
## Valor devuelto  
 Prototipo del argumento `object`.  El prototipo también es un objeto.  
  
## Excepciones  
 Si el argumento `object` no es un objeto, se produce una excepción `TypeError`.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso de la función `Object.getPrototypeOf`.  
  
```javascript  
// Create a constructor function.  
function Pasta(grain, width) {  
    this.grain = grain;  
    this.width = width;  
}  
// Create an object from the pasta constructor.  
var spaghetti = new Pasta("wheat", 0.2);  
  
// Obtain the prototype from the object.  
var proto = Object.getPrototypeOf(spaghetti);  
  
// Add a property to the prototype and validate that  
// the original object has the property.  
proto.foodgroup = "carbohydrates";  
document.write(spaghetti.foodgroup + " ");  
  
// Verify that the prototype obtained from the object  
// is the same as the prototype of the constructor.  
var result = (proto === Pasta.prototype);  
document.write(result + " ");  
  
// Verify that prototype obtained from the object  
// is a prototype of the original object.  
var result = proto.isPrototypeOf(spaghetti);  
document.write(result);  
  
// Output: carbohydrates true true  
```  
  
## Ejemplo  
 En el ejemplo siguiente se utiliza la función `Object.getPrototypeOf` para validar los tipos de datos.  
  
```javascript  
var reg = /a/;  
var result = (Object.getPrototypeOf(reg) === RegExp.prototype);  
document.write(result + " ");  
  
var err = new Error("an error");  
var result = (Object.getPrototypeOf(err) === Error.prototype);  
document.write(result);  
  
// Output: true true  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vea también  
 [prototype \(Propiedad, Object\)](../../javascript/reference/prototype-property-object-javascript.md)   
 [isPrototypeOf \(Método, Object\)](../../javascript/reference/isprototypeof-method-object-javascript.md)