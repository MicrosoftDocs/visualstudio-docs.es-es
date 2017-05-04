---
title: "Object.keys (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "keys (método) [JavaScript]"
  - "Object.keys (método) [JavaScript]"
ms.assetid: cf4a7daf-cf28-4467-bc6b-f7f106ec3876
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Object.keys (Funci&#243;n de JavaScript)
Devuelve los nombres de las propiedades y los métodos enumerables de un objeto.  
  
## Sintaxis  
  
```javascript  
Object.keys(object)  
```  
  
#### Parámetros  
  
|Parámetro|Definición|  
|---------------|----------------|  
|`object`|Obligatorio.  Objeto que contiene las propiedades y los métodos.  Puede ser un objeto que tú creaste o un objeto existente de Document Object Model \(DOM\).|  
  
## Valor devuelto  
 Matriz que contiene los nombres de las propiedades y los métodos enumerables del objeto.  
  
## Excepciones  
 Si el valor proporcionado para el argumento `object` no es el nombre de un objeto, se produce una excepción `TypeError`.  
  
## Comentarios  
 El método `keys` solo devuelve los nombres de propiedades y métodos enumerables.  Para devolver los nombres de las propiedades y los métodos enumerables y no enumerables, puedes usar [Object.getOwnPropertyNames \(Función\)](../../javascript/reference/object-getownpropertynames-function-javascript.md).  
  
 Para obtener información sobre el atributo `enumerable` de una propiedad, consulta [Object.defineProperty \(Función\)](../../javascript/reference/object-defineproperty-function-javascript.md) y [Object.getOwnPropertyDescriptor \(Función\)](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## Ejemplo  
 En el ejemplo siguiente se crea un objeto que tiene tres propiedades y un método.  Después usa el método `keys` para obtener las propiedades y los métodos del objeto.  
  
```javascript  
// Create a constructor function.  
function Pasta(grain, width, shape) {  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
  
    // Define a method.  
    this.toString = function () {  
        return (this.grain + ", " + this.width + ", " + this.shape);  
    }  
}  
  
// Create an object.  
var spaghetti = new Pasta("wheat", 0.2, "circle");  
  
// Put the enumerable properties and methods of the object in an array.  
var arr = Object.keys(spaghetti);  
document.write (arr);  
  
// Output:  
// grain,width,shape,toString  
```  
  
## Ejemplo  
 En el ejemplo siguiente se muestran los nombres de todas las propiedades enumerables que comienzan por la letra "g" en el objeto Pasta.  
  
```javascript  
// Create a constructor function.  
function Pasta(grain, width, shape) {  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
}  
  
var polenta = new Pasta("corn", 1, "mush");  
  
var keys = Object.keys(polenta).filter(CheckKey);  
document.write(keys);  
  
// Check whether the first character of a string is "g".  
function CheckKey(value) {  
    var firstChar = value.substr(0, 1);  
    if (firstChar.toLowerCase() == "g")  
        return true;  
    else  
        return false;  
}  
  
// Output:  
// grain  
```  
  
## Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vea también  
 [Object.getOwnPropertyNames \(Función\)](../../javascript/reference/object-getownpropertynames-function-javascript.md)