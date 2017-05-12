---
title: "map (M&#233;todo, Array de JavaScript) | Microsoft Docs"
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
  - "matrices [JavaScript], map (método)"
  - "map (método) [JavaScript]"
ms.assetid: 500dc4f8-d73d-4a28-a5b8-c9bd5674ea36
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# map (M&#233;todo, Array de JavaScript)
Llama a una función de devolución de llamada definida para cada elemento de una matriz y devuelve una matriz que contiene los resultados.  
  
## Sintaxis  
  
```  
  
array1.map(callbackfn[, thisArg])  
```  
  
#### Parámetros  
  
|Parámetro|Definición|  
|---------------|----------------|  
|`array1`|Obligatorio.  Objeto de matriz.|  
|`callbackfn`|Obligatorio.  Función que acepta un máximo de tres argumentos.  El método `map` llama a la función `callbackfn` una vez para cada elemento de la matriz.|  
|`thisArg`|Opcional.  Objeto al que puede hacer referencia la palabra clave `this` en la función `callbackfn`.  Si se omite `thisArg`, se usa `undefined` como valor `this`.|  
  
## Valor devuelto  
 Nueva matriz en la que cada elemento es el valor devuelto de la función de devolución de llamada para el elemento de matriz original asociado.  
  
## Excepciones  
 Si el argumento `callbackfn` no es un objeto de función, se produce una excepción `TypeError`.  
  
## Comentarios  
 El método `map` llama a la función `callbackfn` una vez para cada elemento de la matriz, en orden de índice ascendente.  Para los elementos que faltan en la matriz, no se llama a la función de devolución de llamada.  
  
 Además de los objetos Array, cualquier objeto que tenga una propiedad `length` y que tenga nombres de propiedad indizados numéricamente puede usar el método `map`.  
  
## Sintaxis de la función de devolución de llamada  
 La sintaxis de la función de devolución de llamada es la siguiente:  
  
 `function callbackfn(value, index, array1)`  
  
 Puede declarar la función de devolución de llamada con un máximo de hasta tres parámetros.  
  
 En la tabla siguiente se muestran los parámetros de la función de devolución de llamada.  
  
|Argumento de devolución de llamada|Definición|  
|----------------------------------------|----------------|  
|`value`|Valor del elemento de la matriz.|  
|`index`|Índice numérico del elemento de la matriz.|  
|`array1`|Objeto Array que contiene el elemento.|  
  
## Modificar el objeto Array  
 La función de devolución de llamada puede modificar el objeto Array.  
  
 En la tabla siguiente se describen los resultados de modificar el objeto Array después de que se inicie el método `map`.  
  
|Condición después del inicio del método `map`|¿Se pasó el elemento a la función de devolución de llamada?|  
|---------------------------------------------------|-----------------------------------------------------------------|  
|El elemento se agrega más allá de la longitud original de la matriz.|No.|  
|El elemento se agrega para rellenar un elemento que falta en la matriz.|Sí, si ese índice todavía no se pasó a la función de devolución de llamada.|  
|Se cambia el elemento.|Sí, si ese elemento todavía no se pasó a la función de devolución de llamada.|  
|El elemento se elimina de la matriz.|No, a menos que el elemento se haya pasado ya a la función de devolución de llamada.|  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `map`.  
  
```javascript  
// Define the callback function.  
function AreaOfCircle(radius) {  
    var area = Math.PI * (radius * radius);  
    return area.toFixed(0);  
}  
  
// Create an array.  
var radii = [10, 20, 30];  
  
// Get the areas from the radii.  
var areas = radii.map(AreaOfCircle);  
  
document.write(areas);  
  
// Output:  
// 314,1257,2827  
```  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del argumento `thisArg`, que especifica un objeto al que puede hacer referencia la palabra clave `this`.  
  
```javascript  
// Define an object that contains a divisor property and  
// a remainder function.  
var obj = {  
    divisor: 10,  
    remainder: function (value) {  
        return value % this.divisor;  
    }  
}  
  
// Create an array.  
var numbers = [6, 12, 25, 30];  
  
// Get the remainders.  
// The obj argument specifies the this value in the callback function.  
var result = numbers.map(obj.remainder, obj);  
document.write(result);  
  
// Output:  
// 6,2,5,0  
```  
  
## Ejemplo  
 En el ejemplo siguiente se usa un método de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] integrado como la función de devolución de llamada.  
  
```javascript  
// Apply Math.sqrt(value) to each element in an array.  
var numbers = [9, 16];  
var result = numbers.map(Math.sqrt);  
  
document.write(result);  
// Output: 3,4  
```  
  
## Ejemplo  
 El método `map` se puede aplicar a una cadena.  Esto se ilustra en el siguiente ejemplo:  
  
```javascript  
// Define the callback function.  
function threeChars(value, index, str) {  
    // Create a string that contains the previous, current,  
    // and next character.  
    return str.substring(index - 1, index + 2);  
}  
  
// Create a string.  
var word = "Thursday";  
  
// Apply the map method to the string.  
// Each array element in the result contains a string that  
// has the previous, current, and next character.  
// The commented out statement shows an alternative syntax.  
var result = [].map.call(word, threeChars);  
// var result = Array.prototype.map.call(word, threeChars);  
  
document.write(result);  
  
// Output:  
// Th,Thu,hur,urs,rsd,sda,day,ay  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vea también  
 [Métodos de JavaScript](../../javascript/reference/javascript-methods.md)   
 [Array \(Objeto\)](../../javascript/reference/array-object-javascript.md)   
 [Utilizar matrices](../../javascript/advanced/using-arrays-javascript.md)   
 [filter \(Método, Array\)](../../javascript/reference/filter-method-array-javascript.md)   
 [forEach \(Método, Array\)](../../javascript/reference/foreach-method-array-javascript.md)   
 [Aplicación de ejemplo Hilo JavaScript \(Tienda Windows\)](http://hilojs.codeplex.com/SourceControl/latest)