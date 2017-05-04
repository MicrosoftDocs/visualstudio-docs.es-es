---
title: "reduce (M&#233;todo, Array de JavaScript) | Microsoft Docs"
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
  - "matrices [JavaScript], reduce (método)"
  - "función de devolución de llamada, reduce (método) [JavaScript]"
  - "reduce (método) [JavaScript]"
ms.assetid: 48d069e0-e083-494f-86d5-d459d2377dc5
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# reduce (M&#233;todo, Array de JavaScript)
Llama a la función de devolución de llamada especificada para todos los elementos de una matriz.  El valor devuelto de la función de devolución de llamada es el resultado acumulado, y se proporciona como argumento en la siguiente llamada a dicha función.  
  
## Sintaxis  
  
```  
  
array1.reduce(callbackfn[, initialValue])  
```  
  
#### Parámetros  
  
|Parámetro|Definición|  
|---------------|----------------|  
|`array1`|Obligatorio.  Objeto de matriz.|  
|`callbackfn`|Obligatorio.  Función que acepta hasta cuatro argumentos.  El método `reduce` llama a la función `callbackfn` una vez para cada elemento de la matriz.|  
|`initialValue`|Opcional.  Si se especifica `initialValue`, se usa como valor inicial para iniciar la acumulación.  La primera llamada a la función `callbackfn` proporciona este valor como un argumento en lugar de un valor de matriz.|  
  
## Valor devuelto  
 Resultado acumulado de la última llamada a la función de devolución de llamada.  
  
## Excepciones  
 Se produce una excepción `TypeError` cuando se cumple cualquiera de las condiciones siguientes:  
  
-   El argumento `callbackfn` no es un objeto de función.  
  
-   La matriz no contiene ningún elemento y no se proporciona `initialValue`.  
  
## Comentarios  
 Si se proporciona `initialValue`, el método `reduce` llama a la función `callbackfn` una vez para cada elemento presente en la matriz, en orden de índice ascendente.  Si `initialValue` no se proporciona, el método `reduce` llama a la función `callbackfn` en cada elemento, empezando por el segundo elemento.  
  
 El valor devuelto de la función de devolución de llamada se proporciona como argumento `previousValue` en la siguiente llamada a la función de devolución de llamada.  El valor devuelto de la última llamada a la función de devolución de llamada es el valor devuelto del método `reduce`.  
  
 Para los elementos que faltan en la matriz, no se llama a la función de devolución de llamada.  
  
> [!NOTE]
>  [reduceRight \(Método, Array\)](../../javascript/reference/reduceright-method-array-javascript.md) procesa los elementos en orden de índice descendente.  
  
## Sintaxis de la función de devolución de llamada  
 La sintaxis de la función de devolución de llamada es la siguiente:  
  
 `function callbackfn(previousValue, currentValue, currentIndex, array1)`  
  
 Puedes declarar la función de devolución de llamada usando hasta cuatro parámetros.  
  
 En la tabla siguiente se muestran los parámetros de la función de devolución de llamada.  
  
|Argumento de devolución de llamada|Definición|  
|----------------------------------------|----------------|  
|`previousValue`|Valor de la llamada anterior a la función de devolución de llamada.  Si se proporciona `initialValue` al método `reduce`, `previousValue` es `initialValue` la primera vez que se llama a la función.|  
|`currentValue`|Valor del elemento de matriz actual.|  
|`currentIndex`|Índice numérico del elemento de matriz actual.|  
|`array1`|Objeto Array que contiene el elemento.|  
  
## Primera llamada a la función de devolución de llamada  
 La primera vez que se llama a la función de devolución de llamada, los valores proporcionados como argumentos dependen de si el método `reduce` tiene un argumento `initialValue`.  
  
 Si se proporciona `initialValue` al método reduce:  
  
-   El argumento `previousValue` es `initialValue`.  
  
-   El argumento `currentValue` es el valor del primer elemento presente en la matriz.  
  
 Si no se proporciona `initialValue`:  
  
-   El argumento `previousValue` es el valor del primer elemento presente en la matriz.  
  
-   El argumento `currentValue` es el valor del segundo elemento presente en la matriz.  
  
## Modificar el objeto Array  
 La función de devolución de llamada puede modificar el objeto Array.  
  
 En la tabla siguiente se describen los resultados de modificar el objeto Array después de que se inicie el método `reduce`.  
  
|Condición después del inicio del método `reduce`|¿Se pasó el elemento a la función de devolución de llamada?|  
|------------------------------------------------------|-----------------------------------------------------------------|  
|El elemento se agrega más allá de la longitud original de la matriz.|No.|  
|El elemento se agrega para rellenar un elemento que falta en la matriz.|Sí, si ese índice todavía no se pasó a la función de devolución de llamada.|  
|Se cambia el elemento.|Sí, si ese elemento todavía no se pasó a la función de devolución de llamada.|  
|El elemento se elimina de la matriz.|No, a menos que el elemento se haya pasado ya a la función de devolución de llamada.|  
  
## Ejemplo  
 En el ejemplo siguiente se concatenan valores de matriz en una cadena, separando los valores con "::".  Como no se proporciona ningún valor inicial al método `reduce`, la primera llamada a la función de devolución de llamada tiene "abc" como argumento `previousValue` y "def" como argumento `currentValue`.  
  
```javascript  
// Define the callback function.  
function appendCurrent (previousValue, currentValue) {  
    return previousValue + "::" + currentValue;  
    }  
  
// Create an array.  
var elements = ["abc", "def", 123, 456];  
  
// Call the reduce method, which calls the callback function  
// for each array element.  
var result = elements.reduce(appendCurrent);  
  
document.write(result);  
  
// Output:  
//  abc::def::123::456  
  
```  
  
## Ejemplo  
 En el ejemplo siguiente se suman los valores de una matriz después de haberse redondeado.  Se llama al método `reduce` con un valor inicial de 0.  
  
```javascript  
// Define the callback function.  
function addRounded (previousValue, currentValue) {  
    return previousValue + Math.round(currentValue);  
    }  
  
// Create an array.  
var numbers = [10.9, 15.4, 0.5];  
  
// Call the reduce method, starting with an initial value of 0.  
var result = numbers.reduce(addRounded, 0);  
  
document.write (result);  
// Output: 27  
```  
  
## Ejemplo  
 En el ejemplo siguiente se suman los valores de una matriz.  Se usan los parámetros `currentIndex` y `array1` en la función de devolución de llamada.  
  
```javascript  
function addDigitValue(previousValue, currentDigit, currentIndex, array) {  
    var exponent = (array.length - 1) - currentIndex;  
    var digitValue = currentDigit * Math.pow(10, exponent);  
    return previousValue + digitValue;  
    }  
  
var digits = [4, 1, 2, 5];  
  
// Determine an integer that is computed from values in the array.  
var result = digits.reduce(addDigitValue, 0);  
  
document.write (result);  
// Output: 4125  
```  
  
## Ejemplo  
 En el ejemplo siguiente se obtiene una matriz que solo contiene los valores comprendidos entre 1 y 10 en otra matriz.  El valor inicial proporcionado al método `reduce` es una matriz vacía.  
  
```javascript  
function Process(previousArray, currentValue) {  
    // If currentValue is between 1 and 10,   
    // append currentValue to the array.  
    var nextArray;  
    if (currentValue >= 1 && currentValue <= 10)  
        nextArray = previousArray.concat(currentValue);  
    else  
        nextArray = previousArray;  
  
    // If this is not the last call by the reduce method,  
    // the returned array is previousArray on the next call.  
    // If this is the last call by the reduce method, the  
    // returned array is the return value of the reduce method.  
    return nextArray;  
}  
  
// Create an array.  
var numbers = [20, 1, -5, 6, 50, 3];  
  
// Call the reduce method, starting with an initial empty array.  
var emptyArray = new Array();  
var resultArray = numbers.reduce(Process, emptyArray);  
  
document.write("result array=" + resultArray);  
  
// Output:  
// result array=1,6,3  
```  
  
## Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vea también  
 [reduceRight \(Método, Array\)](../../javascript/reference/reduceright-method-array-javascript.md)