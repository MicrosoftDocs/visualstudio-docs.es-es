---
title: filtrar (método, Array) (JavaScript) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arrays [JavaScript], filter method
- filter method [JavaScript]
ms.assetid: 1d260370-9e6e-43fc-870f-2d35850db7ee
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33a08fdba38de558dabc749a634fb9b69c52c98a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637785"
---
# <a name="filter-method-array-javascript"></a>filter (Método, Array, JavaScript)
Devuelve los elementos de una matriz que cumplen la condición especificada en una función de devolución de llamada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
array1.filter(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Definición|  
|---------------|----------------|  
|`array1`|Obligatorio. Objeto de matriz.|  
|`callbackfn`|Obligatorio. Función que acepta un máximo de tres argumentos. El método `filter` llama a la función `callbackfn` una vez para cada elemento de la matriz.|  
|`thisArg`|Opcional. Objeto al que puede hacer referencia la palabra clave `this` en la función `callbackfn`. Si se omite `thisArg`, se usa `undefined` como valor `this`.|  
  
## <a name="return-value"></a>Valor devuelto  
 Nueva matriz que contiene todos los valores que devuelve la función de devolución de llamada `true`. Si la función de devolución de llamada devuelve `false` para todos los elementos de `array1`, la longitud de la nueva matriz es 0.  
  
## <a name="exceptions"></a>Excepciones  
 Si el argumento `callbackfn` no es un objeto de función, se produce una excepción `TypeError`.  
  
## <a name="remarks"></a>Comentarios  
 El método `filter` llama a la función `callbackfn` una vez para cada elemento de la matriz, en orden de índice ascendente. Para los elementos que faltan en la matriz, no se llama a la función de devolución de llamada.  
  
 Además de los objetos Array, cualquier objeto que tenga una propiedad `filter` y que tenga nombres de propiedad indizados numéricamente puede usar el método `length`.  
  
## <a name="callback-function-syntax"></a>Sintaxis de la función de devolución de llamada  
 La sintaxis de la función de devolución de llamada es la siguiente:  
  
 `function callbackfn(value, index, array1)`  
  
 Puede declarar la función de devolución de llamada con un máximo de hasta tres parámetros.  
  
 En la tabla siguiente se muestran los parámetros de la función de devolución de llamada.  
  
|Argumento de devolución de llamada|Definición|  
|-----------------------|----------------|  
|`value`|Valor del elemento de la matriz.|  
|`index`|Índice numérico del elemento de la matriz.|  
|`array1`|Objeto Array que contiene el elemento.|  
  
## <a name="modifying-the-array-object"></a>Modificar el objeto Array  
 El método `filter` no modifica directamente la matriz original, pero la función de devolución de llamada puede modificarla. En la tabla siguiente se describen los resultados de modificar el objeto Array después de que se inicie el método `filter`.  
  
|Condición después del inicio del método `filter`|¿Se pasó el elemento a la función de devolución de llamada?|  
|------------------------------------------------|------------------------------------------|  
|El elemento se agrega más allá de la longitud original de la matriz.|No.|  
|El elemento se agrega para rellenar un elemento que falta en la matriz.|Sí, si ese índice todavía no se pasó a la función de devolución de llamada.|  
|Se cambia el elemento.|Sí, si ese elemento todavía no se pasó a la función de devolución de llamada.|  
|El elemento se elimina de la matriz.|No, a menos que el elemento se haya pasado ya a la función de devolución de llamada.|  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo, se muestra cómo utilizar el método `filter`.  
  
```JavaScript  
// Define a callback function.  
function CheckIfPrime(value, index, ar) {  
    high = Math.floor(Math.sqrt(value)) + 1;  
  
    for (var div = 2; div <= high; div++) {  
        if (value % div == 0) {  
            return false;  
        }  
    }   
    return true;  
}  
  
// Create the original array.  
var numbers = [31, 33, 35, 37, 39, 41, 43, 45, 47, 49, 51, 53];  
  
// Get the prime numbers that are in the original array.   
var primes = numbers.filter(CheckIfPrime);  
  
document.write(primes);  
// Output: 31,37,41,43,47,53  
```  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo, el argumento `callbackfn` incluye el código de la función de devolución de llamada.  
  
```JavaScript  
// Create the original array.  
var arr = [5, "element", 10, "the", true];  
  
// Create an array that contains the string  
// values that are in the original array.  
var result = arr.filter(  
    function (value) {  
        return (typeof value === 'string');  
    }  
);  
  
document.write(result);  
// Output: element, the  
```  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra los nombres de propiedades que comiencen con la letra "css" en la `window` objeto DOM.  
  
```JavaScript  
var filteredNames = Object.getOwnPropertyNames(window).filter(IsC);  
  
    for (i in filteredNames)  
        document.write(filteredNames[i] + "<br/>");  
  
// Check whether the string starts with "css".  
function IsC(value) {  
    var firstChar = value.substr(0, 3);  
    if (firstChar.toLowerCase() == "css")  
        return true;  
    else  
        return false;  
    }  
  
// Output:  
// CSSRule  
// CSSFontFaceRule  
// CSSImportRule  
// CSSMediaRule  
// CSSNamespaceRule  
// CSSPageRule  
// CSSRuleList  
// CSSStyleDeclaration  
// CSSStyleRule  
// CSSStyleSheet  
  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso del argumento `thisArg`, que especifica un objeto al que puede hacer referencia la palabra clave `this`.  
  
```JavaScript  
var checkNumericRange = function(value) {  
    if (typeof value !== 'number')  
        return false;  
    else   
        return value >= this.minimum && value <= this.maximum;  
}  
  
var numbers = [6, 12, "15", 16, "the", -12];  
  
// The obj argument enables use of the this value  
// within the callback function.  
var obj = { minimum: 10, maximum: 20 }  
  
var result = numbers.filter(checkNumericRange, obj);  
  
document.write(result);  
// Output: 12,16  
  
```  
  
## <a name="example"></a>Ejemplo  
 El `filter` método puede aplicarse a una cadena en lugar de una matriz. En el ejemplo siguiente se muestra cómo hacerlo.  
  
```JavaScript  
// Define a callback function that returns true  
// if the current array element follows a space  
// or is the first character.  
function CheckValue(value, index, ar) {  
    if (index == 0)  
        return true;  
    else  
        return ar[index - 1] === " ";  
}  
  
// Create a string.  
var sentence = "The quick brown fox jumps over the lazy dog.";   
  
// Create an array that contains all characters that follow a space.  
var subset = [].filter.call(sentence, CheckValue);   
  
// You can use this alternative syntax.  
//var subset = Array.prototype.filter.call(sentence, CheckValue);  
  
document.write(subset);  
// Output: T,q,b,f,j,o,t,l,d  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Array (objeto)](../../javascript/reference/array-object-javascript.md)   
 [Usar matrices](../../javascript/advanced/using-arrays-javascript.md)   
 [Map (método, Array)](../../javascript/reference/map-method-array-javascript.md)   
 [forEach (Método, Array)](../../javascript/reference/foreach-method-array-javascript.md)