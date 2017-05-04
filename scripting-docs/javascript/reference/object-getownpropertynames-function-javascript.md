---
title: "Object.getOwnPropertyNames (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "getOwnPropertyNames (método) [JavaScript]"
  - "Object.getOwnPropertyNames (método) [JavaScript]"
ms.assetid: 59f4b6b1-02be-44b3-a06c-a5ca8f70c3d8
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Object.getOwnPropertyNames (Funci&#243;n de JavaScript)
Devuelve los nombres de las propiedades propias de un objeto.  Las propiedades propias de un objeto son aquellas definidas directamente en ese objeto, y no se heredan del prototipo del objeto.  Las propiedades de un objeto incluyen tanto campos \(objetos\) como funciones.  
  
## Sintaxis  
  
```javascript  
Object.getOwnPropertyNames(object)  
```  
  
#### Parámetros  
  
|Parámetro|Definición|  
|---------------|----------------|  
|`object`|Obligatorio.  Objeto que contiene las propiedades propias.|  
  
## Valor devuelto  
 Matriz que contiene los nombres de las propiedades propias del objeto.  
  
## Excepciones  
 Si el valor proporcionado para el argumento `object` no es el nombre de un objeto, se produce una excepción `TypeError`.  
  
## Comentarios  
 El método `getOwnPropertyNames` devuelve los nombres de propiedades y métodos tanto enumerables como no enumerables.  Para devolver solo los nombres de propiedades y métodos enumerables, puedes usar [Object.keys \(Función\)](../../javascript/reference/object-keys-function-javascript.md).  
  
## Ejemplo  
 En el ejemplo siguiente se crea un objeto que tiene tres propiedades y un método.  Después se usa el método `getOwnPropertyNames` para obtener las propiedades propias \(incluido el método\) del objeto.  
  
```javascript  
function Pasta(grain, width, shape) {  
    // Define properties.  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
    this.toString = function () {  
        return (this.grain + ", " + this.width + ", " + this.shape);  
    }  
}  
  
// Create an object.  
var spaghetti = new Pasta("wheat", 0.2, "circle");  
  
// Get the own property names.  
var arr = Object.getOwnPropertyNames(spaghetti);  
document.write (arr);  
  
// Output:  
//   grain,width,shape,toString  
```  
  
## Ejemplo  
 En el ejemplo siguiente se muestran los nombres de las propiedades que comienzan por la letra 's' en un objeto spaghetti construido con el constructor Pasta.  
  
```javascript  
function Pasta(grain, size, shape) {  
    this.grain = grain;   
    this.size = size;   
    this.shape = shape;   
}  
  
var spaghetti = new Pasta("wheat", 2, "circle");  
  
var names = Object.getOwnPropertyNames(spaghetti).filter(CheckKey);  
document.write(names);   
  
// Check whether the first character of a string is 's'.   
function CheckKey(value) {  
    var firstChar = value.substr(0, 1);   
    if (firstChar.toLowerCase() == 's')  
        return true;   
    else  
         return false;   
}  
// Output:  
// size,shape  
```  
  
## Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vea también  
 [Object.keys \(Función\)](../../javascript/reference/object-keys-function-javascript.md)