---
title: "forEach (M&#233;todo, Array de JavaScript) | Microsoft Docs"
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
  - "matrices [JavaScript], forEach (método)"
  - "función de devolución de llamada, forEach (método) [JavaScript]"
  - "forEach (método) [JavaScript]"
ms.assetid: bd188034-a62b-4cbd-99c8-46d70dd6823d
caps.latest.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 28
---
# forEach (M&#233;todo, Array de JavaScript)
Realiza la acción especificada para cada elemento de una matriz.  
  
## Sintaxis  
  
```  
  
array1.forEach(callbackfn[, thisArg])  
```  
  
#### Parámetros  
  
|Parámetro|Definición|  
|---------------|----------------|  
|`array1`|Obligatorio.  Objeto de matriz.|  
|`callbackfn`|Obligatorio.  Función que acepta un máximo de tres argumentos.  `forEach` llama a la función `callbackfn` una vez para cada elemento de la matriz.|  
|`thisArg`|Opcional.  Objeto al que puede hacer referencia la palabra clave `this` en la función `callbackfn`.  Si se omite `thisArg`, se usa `undefined` como valor `this`.|  
  
## Excepciones  
 Si el argumento `callbackfn` no es un objeto de función, se produce una excepción `TypeError`.  
  
## Comentarios  
 El método `forEach` llama a la función `callbackfn` una vez para cada elemento presente en la matriz, en orden de índice ascendente.  Para los elementos que faltan en la matriz, no se llama a la función de devolución de llamada.  
  
 Además de los objetos Array, cualquier objeto que tenga una propiedad `length` y que tenga nombres de propiedad indizados numéricamente puede usar el método `forEach`.  
  
## Sintaxis de la función de devolución de llamada  
 La sintaxis de la función de devolución de llamada es la siguiente:  
  
 `function callbackfn(value, index, array1)`  
  
 Puede declarar la función de devolución de llamada con un máximo de hasta tres parámetros.  
  
 Los parámetros de la función de devolución de llamada son los siguientes.  
  
|Argumento de devolución de llamada|Definición|  
|----------------------------------------|----------------|  
|`value`|Valor del elemento de la matriz.|  
|`index`|Índice numérico del elemento de la matriz.|  
|`array1`|Objeto Array que contiene el elemento.|  
  
## Modificar el objeto Array  
 El método `forEach` no modifica directamente la matriz original, pero la función de devolución de llamada puede modificarla.  En la tabla siguiente se describen los resultados de modificar el objeto Array después de que se inicie el método `forEach`.  
  
|Condición después del inicio del método `forEach`|¿Se pasó el elemento a la función de devolución de llamada?|  
|-------------------------------------------------------|-----------------------------------------------------------------|  
|El elemento se agrega más allá de la longitud original de la matriz.|No.|  
|El elemento se agrega para rellenar un elemento que falta en la matriz.|Sí, si ese índice todavía no se pasó a la función de devolución de llamada.|  
|Se cambia el elemento.|Sí, si ese elemento todavía no se pasó a la función de devolución de llamada.|  
|El elemento se elimina de la matriz.|No, a menos que el elemento se haya pasado ya a la función de devolución de llamada.|  
  
## Ejemplo  
 En el siguiente ejemplo, se muestra el uso del método `forEach`.  
  
```javascript  
// Define the callback function.  
function ShowResults(value, index, ar) {  
    document.write("value: " + value);  
    document.write(" index: " + index);  
    document.write("<br />");  
}  
  
// Create an array.  
var letters = ['ab', 'cd', 'ef'];  
  
// Call the ShowResults callback function for each  
// array element.  
letters.forEach(ShowResults);  
  
// Output:  
//  value: ab index: 0   
//  value: cd index: 1   
//  value: ef index: 2   
```  
  
## Ejemplo  
 En el siguiente ejemplo, el argumento `callbackfn` incluye el código de la función de devolución de llamada.  
  
```javascript  
// Create an array.  
var numbers = [10, 11, 12];  
  
// Call the addNumber callback function for each array element.  
var sum = 0;  
numbers.forEach(  
    function addNumber(value) { sum += value; }  
);  
  
document.write(sum);  
// Output: 33  
  
```  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del argumento `thisArg`, que especifica un objeto al que se puede hacer referencia con la palabra clave `this`.  
  
```javascript  
// Define the object that contains the callback function.  
var obj = {  
    showResults: function(value, index) {  
        // Call calcSquare by using the this value.  
        var squared = this.calcSquare(value);  
  
        document.write("value: " + value);  
        document.write(" index: " + index);  
        document.write(" squared: " + squared);  
        document.write("<br />");  
    },  
    calcSquare: function(x) { return x * x }  
};  
  
// Define an array.  
var numbers = [5, 6];  
  
// Call the showResults callback function for each array element.  
// The obj is the this value within the   
// callback function.  
numbers.forEach(obj.showResults, obj);  
  
// Embed the callback function in the forEach statement.  
// The obj argument is the this value within the obj object.  
// The output is the same as for the previous statement.  
numbers.forEach(function(value, index) { this.showResults(value, index) }, obj);  
  
// Output:  
//  value: 5 index: 0 squared: 25  
//  value: 6 index: 1 squared: 36  
//  value: 5 index: 0 squared: 25  
//  value: 6 index: 1 squared: 36  
```  
  
## Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vea también  
 [filter \(Método, Array\)](../../javascript/reference/filter-method-array-javascript.md)   
 [map \(Método, Array\)](../../javascript/reference/map-method-array-javascript.md)   
 [some \(Método, Array\)](../../javascript/reference/some-method-array-javascript.md)   
 [Array \(Objeto\)](../../javascript/reference/array-object-javascript.md)   
 [Utilizar matrices](../../javascript/advanced/using-arrays-javascript.md)   
 [Aplicación de ejemplo Hilo JavaScript \(Tienda Windows\)](http://hilojs.codeplex.com/SourceControl/latest)