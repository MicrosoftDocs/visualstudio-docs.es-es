---
title: "reducir (método, Array) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- callback function, reduce method [JavaScript]
- arrays [JavaScript], reduce method
- reduce method [JavaScript]
ms.assetid: 48d069e0-e083-494f-86d5-d459d2377dc5
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76279f66f8e3180fdebd73b83eb31c7368cefc75
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="reduce-method-array-javascript"></a>reduce (Método, Array de JavaScript)
Llama a la función de devolución de llamada especificado para todos los elementos de una matriz. El valor devuelto de la función de devolución de llamada es el resultado acumulado, y se proporciona como un argumento en la siguiente llamada a dicha función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
array1.reduce(callbackfn[, initialValue])  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Definición|  
|---------------|----------------|  
|`array1`|Obligatorio. Objeto de matriz.|  
|`callbackfn`|Obligatorio. Una función que acepta hasta cuatro argumentos. El método `reduce` llama a la función `callbackfn` una vez para cada elemento de la matriz.|  
|`initialValue`|Opcional. Si `initialValue` se especifica, se utiliza como valor inicial para iniciar la acumulación. La primera llamada a la `callbackfn` función proporciona este valor como argumento en lugar de un valor de matriz.|  
  
## <a name="return-value"></a>Valor devuelto  
 El resultado acumulado desde la última llamada a la función de devolución de llamada.  
  
## <a name="exceptions"></a>Excepciones  
 Un `TypeError` excepción se produce cuando alguna de las condiciones siguientes sea verdadera:  
  
-   El `callbackfn` argumento no es un objeto de función.  
  
-   La matriz no contiene elementos y `initialValue` no se ha proporcionado.  
  
## <a name="remarks"></a>Comentarios  
 Si un `initialValue` se proporciona, el `reduce` llamadas al método el `callbackfn` funcionar una vez por cada elemento presente en la matriz, en orden de índice ascendente. Si un `initialValue` no se proporciona, el `reduce` llamadas al método el `callbackfn` función en cada elemento, empezando por el segundo elemento.  
  
 El valor devuelto de la función de devolución de llamada se proporciona como el `previousValue` argumento en la siguiente llamada a la función de devolución de llamada. El valor devuelto de la última llamada a la función de devolución de llamada es el valor devuelto de la `reduce` método.  
  
 Para los elementos que faltan en la matriz, no se llama a la función de devolución de llamada.  
  
> [!NOTE]
>  El [reduceRight (método, Array)](../../javascript/reference/reduceright-method-array-javascript.md) procesa los elementos en orden de índice descendente.  
  
## <a name="callback-function-syntax"></a>Sintaxis de la función de devolución de llamada  
 La sintaxis de la función de devolución de llamada es la siguiente:  
  
 `function callbackfn(previousValue, currentValue, currentIndex, array1)`  
  
 Puede declarar la función de devolución de llamada mediante el uso de hasta cuatro parámetros.  
  
 En la tabla siguiente se muestran los parámetros de la función de devolución de llamada.  
  
|Argumento de devolución de llamada|Definición|  
|-----------------------|----------------|  
|`previousValue`|El valor de la llamada anterior a la función de devolución de llamada. Si un `initialValue` se proporciona a la `reduce` método, el `previousValue` es `initialValue` la primera vez que se llama a la función.|  
|`currentValue`|El valor del elemento de matriz actual.|  
|`currentIndex`|El índice numérico del elemento de matriz actual.|  
|`array1`|Objeto Array que contiene el elemento.|  
  
## <a name="first-call-to-the-callback-function"></a>Primera llamada a la función de devolución de llamada  
 La primera vez que se llama a la función de devolución de llamada, los valores proporcionados como argumentos dependen de si la `reduce` método tiene un `initialValue` argumento.  
  
 Si un `initialValue` se proporciona al método reduce:  
  
-   El argumento `previousValue` es `initialValue`.  
  
-   El `currentValue` argumento es el valor del primer elemento presente en la matriz.  
  
 Si un `initialValue` no se proporciona:  
  
-   El `previousValue` argumento es el valor del primer elemento presente en la matriz.  
  
-   El `currentValue` argumento es el valor del segundo elemento presente en la matriz.  
  
## <a name="modifying-the-array-object"></a>Modificar el objeto Array  
 La función de devolución de llamada puede modificar el objeto Array.  
  
 En la tabla siguiente se describen los resultados de modificar el objeto Array después de que se inicie el método `reduce`.  
  
|Condición después del inicio del método `reduce`|¿Se pasó el elemento a la función de devolución de llamada?|  
|------------------------------------------------|------------------------------------------|  
|El elemento se agrega más allá de la longitud original de la matriz.|No.|  
|El elemento se agrega para rellenar un elemento que falta en la matriz.|Sí, si ese índice todavía no se pasó a la función de devolución de llamada.|  
|Se cambia el elemento.|Sí, si ese elemento todavía no se pasó a la función de devolución de llamada.|  
|El elemento se elimina de la matriz.|No, a menos que el elemento se haya pasado ya a la función de devolución de llamada.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se concatenan valores de la matriz en una cadena, separe los valores con "::". Dado que se proporciona ningún valor inicial para la `reduce` método, la primera llamada a la función de devolución de llamada tiene "abc" como el `previousValue` argumento y "def" como el `currentValue` argumento.  
  
```JavaScript  
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
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente agrega los valores de una matriz después de que se han redondeado. El `reduce` método se llama con un valor inicial de 0.  
  
```JavaScript  
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
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente agrega los valores en una matriz. El `currentIndex` y `array1` parámetros se usan en la función de devolución de llamada.  
  
```JavaScript  
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
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se obtiene una matriz que contiene únicamente los valores que están comprendidos entre 1 y 10 en otra matriz. El valor inicial proporcionado para el `reduce` método es una matriz vacía.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [reduceRight (Método, Array)](../../javascript/reference/reduceright-method-array-javascript.md)