---
title: "reduceRight (método, Array) (JavaScript) | Documentos de Microsoft"
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
- arrays [JavaScript], reduceRight method
- reduceRight method [JavaScript]
ms.assetid: 85963761-da11-407c-8bce-278c930e61bd
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d7fd2794157eadacefa7404f9333c51aed9425c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="reduceright-method-array-javascript"></a>reduceRight (Método, Array de JavaScript)
Llama a la función de devolución de llamada especificado para todos los elementos de una matriz, en orden descendente. El valor devuelto de la función de devolución de llamada es el resultado acumulado, y se proporciona como un argumento en la siguiente llamada a dicha función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
array1.reduceRight(callbackfn[, initialValue])  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Definición|  
|---------------|----------------|  
|`array1`|Obligatorio. Objeto de matriz.|  
|`callbackfn`|Obligatorio. Una función que acepta hasta cuatro argumentos. El método `reduceRight` llama a la función `callbackfn` una vez para cada elemento de la matriz.|  
|`initialValue`|Opcional. Si `initialValue` se especifica, se utiliza como valor inicial para iniciar la acumulación. La primera llamada a la `callbackfn` función proporciona este valor como argumento en lugar de un valor de matriz.|  
  
## <a name="return-value"></a>Valor devuelto  
 Objeto que contiene el resultado acumulado desde la última llamada a la función de devolución de llamada.  
  
## <a name="exceptions"></a>Excepciones  
 Un `TypeError` excepción se produce cuando alguna de las condiciones siguientes sea verdadera:  
  
-   El `callbackfn` argumento no es un objeto de función.  
  
-   La matriz no contiene elementos y `initialValue` no se ha proporcionado.  
  
## <a name="remarks"></a>Comentarios  
 Si un `initialValue` se proporciona, el `reduceRight` llamadas al método el `callbackfn` funcionar una vez por cada elemento de la matriz, en orden de índice descendente. Si no hay ningún `initialValue` se proporciona, el `reduceRight` llamadas al método el `callbackfn` función en cada elemento, empezando por el elemento del segundo al último, en orden de índice descendente.  
  
 El valor devuelto de la función de devolución de llamada se proporciona como el `previousValue` argumento en la siguiente llamada a la función de devolución de llamada. El valor devuelto de la última llamada a la función de devolución de llamada es el valor devuelto de la `reduceRight` método.  
  
 Para los elementos que faltan en la matriz, no se llama a la función de devolución de llamada.  
  
 Para acumular un resultado en orden de índice ascendente, use la [reducir (método, Array)](../../javascript/reference/reduce-method-array-javascript.md).  
  
## <a name="callback-function-syntax"></a>Sintaxis de la función de devolución de llamada  
 La sintaxis de la función de devolución de llamada es la siguiente:  
  
 `function callbackfn(previousValue, currentValue, currentIndex, array1)`  
  
 Puede declarar la función de devolución de llamada mediante el uso de hasta cuatro parámetros.  
  
 En la tabla siguiente se muestran los parámetros de la función de devolución de llamada.  
  
|Argumento de devolución de llamada|Definición|  
|-----------------------|----------------|  
|`previousValue`|El valor de la llamada anterior a la función de devolución de llamada. Si un `initialValue` se proporciona a la `reduceRight` método, el `previousValue` es `initialValue` la primera vez que se llama a la función.|  
|`currentValue`|El valor del elemento de matriz actual.|  
|`currentIndex`|El índice numérico del elemento de matriz actual.|  
|`array1`|Objeto Array que contiene el elemento.|  
  
## <a name="first-call-to-the-callback-function"></a>Primera llamada a la función de devolución de llamada  
 La primera vez que se llama a la función de devolución de llamada, los valores proporcionados como argumentos dependen de si la `reduceRight` método tiene un `initialValue` argumento.  
  
 Si un `initialValue` se proporciona a los `reduceRight` método:  
  
-   El argumento `previousValue` es `initialValue`.  
  
-   El `currentValue` argumento es el valor del último elemento presente en la matriz.  
  
 Si un `initialValue` no se proporciona:  
  
-   El `previousValue` argumento es el valor del último elemento presente en la matriz.  
  
-   El `currentValue` argumento es el valor del segundo al último elemento presente en la matriz.  
  
## <a name="modifying-the-array-object"></a>Modificar el objeto Array  
 La función de devolución de llamada puede modificar el objeto Array.  
  
 En la tabla siguiente se describen los resultados de modificar el objeto Array después de que se inicie el método `reduceRight`.  
  
|Condición después del inicio del método `reduceRight`|¿Se pasó el elemento a la función de devolución de llamada?|  
|-----------------------------------------------------|------------------------------------------|  
|El elemento se agrega más allá de la longitud original de la matriz.|No.|  
|El elemento se agrega para rellenar un elemento que falta en la matriz.|Sí, si ese índice todavía no se pasó a la función de devolución de llamada.|  
|Se cambia el elemento.|Sí, si ese elemento todavía no se pasó a la función de devolución de llamada.|  
|El elemento se elimina de la matriz.|No, a menos que el elemento se haya pasado ya a la función de devolución de llamada.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se concatenan valores de la matriz en una cadena, separe los valores con "::". Dado que se proporciona ningún valor inicial para la `reduceRight` método, la primera llamada a la función de devolución de llamada tiene 456 como el `previousValue` argumento y 123 como el `currentValue` argumento.  
  
```JavaScript  
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
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se busca la suma de los cuadrados de los elementos de matriz. El `reduceRight` método se llama con un valor inicial de 0.  
  
```JavaScript  
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
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente obtiene los elementos de una matriz cuyos valores están comprendidos entre 1 y 10. El valor inicial proporcionado para el `reduceRight` método es una matriz vacía.  
  
```JavaScript  
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
  
## <a name="example"></a>Ejemplo  
 El método `reduceRight` se puede aplicar a una cadena. En el ejemplo siguiente se muestra cómo utilizar este método para invertir los caracteres de una cadena.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [reduce (Método, Array)](../../javascript/reference/reduce-method-array-javascript.md)