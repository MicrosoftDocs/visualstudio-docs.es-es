---
title: Objetos y matrices (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arrays [JavaScript]
- arrays [JavaScript], objects
ms.assetid: f5106284-1240-4f47-8c3b-5a45e227e5e1
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6776701ba108ae0ecefc2331c2b12272e0c1be19
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569345"
---
# <a name="objects-and-arrays-javascript"></a>Objetos y matrices (JavaScript)
Los objetos de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] son colecciones de propiedades y métodos. Un método es una función que es miembro de un objeto. Una propiedad es un valor o un conjunto de valores (en forma de matriz u objeto) que es miembro de un objeto. [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] admite cuatro tipos de objetos:  
  
-   Objetos intrínsecos, como `Array` y `String`.  
  
-   Los objetos que crea.  
  
-   Objetos host, como `window` y `document`.  
  
-   Objetos ActiveX.  
  
## <a name="expando-properties-and-methods"></a>Propiedades y métodos expando  
 Todos los objetos de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] admiten propiedades y métodos expando, que se pueden agregar y quitar en tiempo de ejecución. Estas propiedades y métodos pueden tener cualquier nombre y se pueden identificar mediante números. Si el nombre de la propiedad o método es un identificador simple, puede escribirse después del nombre del objeto con un punto, como en `myObj.name`, `myObj.age` y `myObj.getAge` en el siguiente código:  
  
```JavaScript  
var myObj = new Object();  
myObj.name = "Fred";  
myObj.age = 42;  
  
myObj.getAge =   
    function () {  
        return this.age;  
    };  
  
document.write(myObj.name);  
document.write("<br/>");  
document.write(myObj.age);  
document.write("<br/>");  
document.write(myObj.getAge());  
  
// Output:  
// Fred  
// 42  
// 42  
  
```  
  
 Si el nombre de la propiedad o método no es un identificador simple o no se conoce cuando se escribe el script, puede usar una expresión entre corchetes para indizar la propiedad. Los nombres de todas las propiedades expando de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] se convierten en cadenas antes de agregarse al objeto:  
  
```JavaScript  
var myObj = new Object();  
  
// Add two expando properties that cannot be written in the  
// object.property syntax.  
// The first contains invalid characters (spaces), so must be  
// written inside square brackets.  
myObj["not a valid identifier"] = "This is the property value";  
  
// The second expando name is a number, so it also must  
// be placed inside square brackets  
myObj[100] = "100";  
```  
  
 Para obtener información acerca de cómo crear un objeto a partir de una definición, consulte [Crear objetos](../javascript/creating-objects-javascript.md).  
  
## <a name="arrays-as-objects"></a>Matrices como objetos  
 En [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], los objetos y matrices se controlan casi idénticamente, porque las matrices simplemente son un tipo especial de objeto. Tanto los objetos como las matrices pueden tener propiedades y métodos.  
  
 Las matrices tienen una propiedad `length` pero los objetos no. Al asignar un valor a un elemento de una matriz cuyo índice es mayor que la longitud (por ejemplo, `myArray[100] = "hello"`), el valor de la propiedad `length` aumenta automáticamente a la nueva longitud. De igual forma, si reduce el valor de la propiedad `length`, se elimina cualquier elemento cuyo índice esté fuera de la longitud de la matriz.  
  
```JavaScript  
// An array with three elements  
var myArray = new Array(3);  
  
// Add some data  
myArray[0] = "Hello";  
myArray[1] = 42;  
myArray[2] = new Date(2000, 1, 1);  
  
document.write("original length is: " + myArray.length);  
document.write("<br/>");  
// Add some expando properties  
myArray.expando = "JavaScript!";  
myArray["another Expando"] = "Windows";  
  
// This will still display 3, since the two expando properties  
// don't affect the length.  
document.write("new length is : " + myArray.length);  
  
// Output:  
// original length is: 3  
// new length is : 3  
  
```  
  
 Las matrices proporcionan métodos para recorrer y manipular miembros. En el ejemplo siguiente se muestra cómo obtener las propiedades de los objetos almacenados en una matriz.  
  
```JavaScript  
var myArray = new Array(3);  
  
// Add some data  
for(var i = 1; i <= 3; i++) {  
    myArray[i] = new Date(2000 + i, 1, 1);  
}  
  
myArray.forEach(function (item) {  
    document.write(item.getFullYear());  
});  
  
// Output:  
// 2001  
// 2002  
// 2003  
```  
  
## <a name="multi-dimensional-arrays"></a>Matrices multidimensionales  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] no admite directamente matrices multidimensionales, pero puede obtener el comportamiento de matrices multidimensionales almacenando matrices en los elementos de otra matriz. (Puede almacenar cualquier tipo de datos dentro de elementos de matriz, incluidas otras matrices). Por ejemplo, en el código siguiente se compila una tabla de multiplicación para los números hasta el 5.  
  
```JavaScript  
// The size of the table.  
var iMaxNum = 5;  
// Loop counters.  
var i, j;  
  
// Set the length of the array to iMaxNum + 1.   
// The first array index is zero, not 1.  
var MultiplicationTable = new Array(iMaxNum + 1);  
  
// Loop for each major number (each row in the table)  
for (i = 1; i <= iMaxNum; i++)  
{  
    // Create the columns in the table  
    MultiplicationTable[i] = new Array(iMaxNum + 1);  
  
    // Fill the row with the results of the multiplication  
    for (j = 1; j <= iMaxNum; j++)  
    {  
        MultiplicationTable[i][j] = i * j;  
    }  
}  
  
document.write(MultiplicationTable[3][4]);  
document.write("<br/>");   
document.write(MultiplicationTable[5][2]);  
document.write("<br/>");  
document.write(MultiplicationTable[1][4]);  
  
// Output:  
// 12  
// 10  
// 4  
  
```