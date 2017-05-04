---
title: "reduceRight (M&#233;todo, Array de JavaScript) | Microsoft Docs"
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
  - "matrices [JavaScript], reduceRight (método)"
  - "reduceRight (método) [JavaScript]"
ms.assetid: 85963761-da11-407c-8bce-278c930e61bd
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# reduceRight (M&#233;todo, Array de JavaScript)
Llama a la función de devolución de llamada especificada para todos los elementos de una matriz, en orden descendente.  El valor devuelto de la función de devolución de llamada es el resultado acumulado, y se proporciona como argumento en la siguiente llamada a dicha función.  
  
## Sintaxis  
  
```  
  
array1.reduceRight(callbackfn[, initialValue])  
```  
  
#### Parámetros  
  
|Parámetro|Definición|  
|---------------|----------------|  
|`array1`|Obligatorio.  Objeto de matriz.|  
|`callbackfn`|Obligatorio.  Función que acepta hasta cuatro argumentos.  El método `reduceRight` llama a la función `callbackfn` una vez para cada elemento de la matriz.|  
|`initialValue`|Opcional.  Si se especifica `initialValue`, se usa como valor inicial para iniciar la acumulación.  La primera llamada a la función `callbackfn` proporciona este valor como un argumento en lugar de un valor de matriz.|  
  
## Valor devuelto  
 Objeto que contiene el resultado acumulado de la última llamada a la función de devolución de llamada.  
  
## Excepciones  
 Se produce una excepción `TypeError` cuando se cumple cualquiera de las condiciones siguientes:  
  
-   El argumento `callbackfn` no es un objeto de función.  
  
-   La matriz no contiene ningún elemento y no se proporciona `initialValue`.  
  
## Comentarios  
 Si se proporciona `initialValue`, el método `reduceRight` llama a la función `callbackfn` una vez para cada elemento presente en la matriz, en orden de índice descendente.  Si no se proporciona ningún `initialValue`, el método `reduceRight` llama a la función `callbackfn` en cada elemento, empezando por el penúltimo elemento, en orden de índice descendente.  
  
 El valor devuelto de la función de devolución de llamada se proporciona como argumento `previousValue` en la siguiente llamada a la función de devolución de llamada.  El valor devuelto de la última llamada a la función de devolución de llamada es el valor devuelto del método `reduceRight`.  
  
 Para los elementos que faltan en la matriz, no se llama a la función de devolución de llamada.  
  
 Para acumular un resultado en orden de índice ascendente, usa [reduce \(Método, Array\)](../../javascript/reference/reduce-method-array-javascript.md).  
  
## Sintaxis de la función de devolución de llamada  
 La sintaxis de la función de devolución de llamada es la siguiente:  
  
 `function callbackfn(previousValue, currentValue, currentIndex, array1)`  
  
 Puedes declarar la función de devolución de llamada usando hasta cuatro parámetros.  
  
 En la tabla siguiente se muestran los parámetros de la función de devolución de llamada.  
  
|Argumento de devolución de llamada|Definición|  
|----------------------------------------|----------------|  
|`previousValue`|Valor de la llamada anterior a la función de devolución de llamada.  Si se proporciona `initialValue` al método `reduceRight`, `previousValue` es `initialValue` la primera vez que se llama a la función.|  
|`currentValue`|Valor del elemento de matriz actual.|  
|`currentIndex`|Índice numérico del elemento de matriz actual.|  
|`array1`|Objeto Array que contiene el elemento.|  
  
## Primera llamada a la función de devolución de llamada  
 La primera vez que se llama a la función de devolución de llamada, los valores proporcionados como argumentos dependen de si el método `reduceRight` tiene un argumento `initialValue`.  
  
 Si se proporciona `initialValue` al método `reduceRight`:  
  
-   El argumento `previousValue` es `initialValue`.  
  
-   El argumento `currentValue` es el valor del último elemento presente en la matriz.  
  
 Si no se proporciona `initialValue`:  
  
-   El argumento `previousValue` es el valor del último elemento presente en la matriz.  
  
-   El argumento `currentValue` es el valor del penúltimo elemento presente en la matriz.  
  
## Modificar el objeto Array  
 La función de devolución de llamada puede modificar el objeto Array.  
  
 En la tabla siguiente se describen los resultados de modificar el objeto Array después de que se inicie el método `reduceRight`.  
  
|Condición después del inicio del método `reduceRight`|¿Se pasó el elemento a la función de devolución de llamada?|  
|-----------------------------------------------------------|-----------------------------------------------------------------|  
|El elemento se agrega más allá de la longitud original de la matriz.|No.|  
|El elemento se agrega para rellenar un elemento que falta en la matriz.|Sí, si ese índice todavía no se pasó a la función de devolución de llamada.|  
|Se cambia el elemento.|Sí, si ese elemento todavía no se pasó a la función de devolución de llamada.|  
|El elemento se elimina de la matriz.|No, a menos que el elemento se haya pasado ya a la función de devolución de llamada.|  
  
## Ejemplo  
 En el ejemplo siguiente se concatenan valores de matriz en una cadena, separando los valores con "::".  Como no se proporciona ningún valor inicial al método `reduceRight`, la primera llamada a la función de devolución de llamada tiene 456 como argumento `previousValue` y 123 como argumento `currentValue`.  
  
```javascript  
// Define the callback function.  
function appendCurrent (previousValue, currentValue) {  
    return previousValue + "::" + currentValue;  
    }  
  
// Create an array.  
var elements = ["abc", "def", 123, 456];  
  
// Call the reduceRight method, which calls the callback function  
// for each array element, in descending index order.  
var result = elements.reduceRight(appendCurrent);  
  
document.write(result);  
  
// Output:  
//  456::123::def::abc  
```  
  
## Ejemplo  
 En el ejemplo siguiente se busca la suma de los cuadrados de los elementos de la matriz.  Se llama al método `reduceRight` con un valor inicial de 0.  
  
```javascript  
// Define the callback function.  
function Process(previousValue, currentValue, index, array) {  
    // Add the previous value to the current value squared.  
    var nextValue = previousValue + (currentValue * currentValue);  
  
    // If this is not the last call by the reduceRight method,  
    // the return value is previousValue on the next call.  
    // If this is the last call by the reduceRight method, the  
    // return value is the return value of the reduceRight method.  
    return nextValue;  
}  
  
// Create an array.  
var numbers = [3, 4, 5];  
  
// Call the reduceRight method with an initial value of 0.  
var sumOfSquares = numbers.reduceRight(Process, 0);  
  
document.write("sum of squares=" + sumOfSquares);  
  
// Output:  
//  sum of squares=50  
```  
  
## Ejemplo  
 En el ejemplo siguiente se obtienen los elementos de una matriz cuyos valores están entre 1 y 10.  El valor inicial proporcionado al método `reduceRight` es una matriz vacía.  
  
```javascript  
function Process2(previousArray, currentValue) {  
    // If currentValue is between 1 and 10,   
    // append currentValue to the array.  
    var nextArray;  
    if (currentValue >= 1 && currentValue <= 10)  
        nextArray = previousArray.concat(currentValue);  
    else  
        nextArray = previousArray;  
  
    // If this is not the last call by the reduceRight method,  
    // the returned array is previousArray on the next call.  
    // If this is the last call by the reduceRight method, the  
    // returned array is the return value of the reduceRight method.  
    return nextArray;  
}  
  
// Create an array.  
var numbers = [20, 1, -5, 6, 50, 3];  
  
// Call the reduceRight method, starting with an empty array.  
var emptyArray = new Array();  
var resultArray = numbers.reduceRight(Process2, emptyArray);  
  
document.write("result array=" + resultArray);  
  
// Output:  
//  result array=3,6,1  
```  
  
## Ejemplo  
 El método `reduceRight` se puede aplicar a una cadena.  En el ejemplo siguiente se muestra cómo usar este método para invertir los caracteres de una cadena.  
  
```javascript  
// Define the callback function.  
function AppendToArray(previousValue, currentValue) {  
    return previousValue + currentValue;  
}  
  
var word = "retupmoc";  
  
// Create a string that reverses the characters of another string.  
// The commented-out statement shows an alternative syntax.  
var result = [].reduceRight.call(word, AppendToArray, "the ");  
// var result = Array.prototype.reduceRight.call(word, AppendToArray, "the ");  
  
document.write(result);  
  
// Output:  
// the computer  
```  
  
## Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vea también  
 [reduce \(Método, Array\)](../../javascript/reference/reduce-method-array-javascript.md)