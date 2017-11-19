---
title: "Some (método) (matriz) (JavaScript) | Documentos de Microsoft"
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
- arrays [JavaScript], some method
- some method [JavaScript]
ms.assetid: 7b6822f9-c406-4f4e-bfec-a93459745992
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba3f855c61daac511bcf7aca6b47f643dda93313
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="some-method-array-javascript"></a>some (Método, Array de JavaScript)
Determina si la función de devolución de llamada especificado devuelve `true` para cualquier elemento de una matriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
array1.some(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Definición|  
|---------------|----------------|  
|`array1`|Obligatorio. Objeto de matriz.|  
|`callbackfn`|Obligatorio. Función que acepta un máximo de tres argumentos. El `some` llamadas al método el `callbackfn` función para cada elemento de `array1` hasta que el `callbackfn` devuelve `true`, o hasta el final de la matriz.|  
|`thisArg`|Opcional. Objeto al que puede hacer referencia la palabra clave `this` en la función `callbackfn`. Si se omite `thisArg`, se usa `undefined` como valor `this`.|  
  
## <a name="return-value"></a>Valor devuelto  
 `true`Si el `callbackfn` función devuelve `true` para cualquier elemento de matriz; en caso contrario, `false`.  
  
## <a name="exceptions"></a>Excepciones  
 Si el argumento `callbackfn` no es un objeto de función, se produce una excepción `TypeError`.  
  
## <a name="remarks"></a>Comentarios  
 El `some` llamadas al método el `callbackfn` función en cada elemento de matriz, en orden ascendente de index, hasta que el `callbackfn` función devuelve `true`. Si un elemento que hace que `callbackfn` para devolver `true` se encuentra, el `some` método vuelve inmediatamente `true`. Si la devolución de llamada no devuelve `true` en todos los elementos, el `some` método `false`.  
  
 Para los elementos que faltan en la matriz, no se llama a la función de devolución de llamada.  
  
 Además de los objetos Array, cualquier objeto que tenga una propiedad `some` y que tenga nombres de propiedad indizados numéricamente puede usar el método `length`.  
  
> [!NOTE]
>  Puede usar el [cada (método, Array)](../../javascript/reference/every-method-array-javascript.md) para comprobar si la función de devolución de llamada devuelve `true` para todos los elementos de una matriz.  
  
## <a name="callback-function-syntax"></a>Sintaxis de la función de devolución de llamada  
 La sintaxis de la función de devolución de llamada es la siguiente:  
  
 `function callbackfn(value, index, array1)`  
  
 Puede declarar la función de devolución de llamada con hasta tres parámetros.  
  
 En la tabla siguiente se muestran los parámetros de la función de devolución de llamada.  
  
|Parámetro de devolución de llamada|Definición|  
|------------------------|----------------|  
|`value`|Valor del elemento de la matriz.|  
|`index`|Índice numérico del elemento de la matriz.|  
|`array1`|Objeto Array que contiene el elemento.|  
  
## <a name="modifying-the-array-object"></a>Modificar el objeto Array  
 La función de devolución de llamada puede modificar el objeto Array.  
  
 En la tabla siguiente se describen los resultados de modificar el objeto Array después de que se inicie el método `some`.  
  
|Condición después del inicio del método `some`|¿Se pasó el elemento a la función de devolución de llamada?|  
|----------------------------------------------|------------------------------------------|  
|El elemento se agrega más allá de la longitud original de la matriz.|No.|  
|El elemento se agrega para rellenar un elemento que falta en la matriz.|Sí, si ese índice todavía no se pasó a la función de devolución de llamada.|  
|Se cambia el elemento.|Sí, si ese elemento todavía no se pasó a la función de devolución de llamada.|  
|El elemento se elimina de la matriz.|No, a menos que el elemento se haya pasado ya a la función de devolución de llamada.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se usa el `some` método para averiguar si los elementos de una matriz son pares.  
  
```JavaScript  
// The callback function.  
function CheckIfEven(value, index, ar) {  
    if (value % 2 == 0)  
        return true;  
}  
  
var numbers = [1, 15, 4, 10, 11, 22];  
  
var evens = numbers.some(CheckIfEven);  
document.write(evens);  
  
// Output:  
// true  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `thisArg` parámetro, que especifica un objeto al que el `this` palabra clave puede hacer referencia. Comprueba si cualquiera de los números de una matriz están fuera del intervalo proporcionado por un objeto pasado  
  
```JavaScript  
// Create a function that returns true if the value is   
// outside the range.  
var isOutsideRange = function (value) {  
    return value < this.minimum || value > this.maximum;  
}  
  
// Create an array of numbers.  
var numbers = [6, 12, 16, 22, -12];  
  
// The range object is to be the 'this' object.  
var range = { minimum: 10, maximum: 20 };  
  
document.write(numbers.some(isOutsideRange, range));  
  
// Output: true  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [cada (método, Array)](../../javascript/reference/every-method-array-javascript.md)   
 [filtrar (método, Array)](../../javascript/reference/filter-method-array-javascript.md)   
 [map (Método, Array)](../../javascript/reference/map-method-array-javascript.md)