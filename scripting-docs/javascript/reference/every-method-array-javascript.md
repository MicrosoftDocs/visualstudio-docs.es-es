---
title: cada (método, Array) (JavaScript) | Documentos de Microsoft
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
- every method
- arrays [JavaScript], every method
ms.assetid: dc4ee2f8-fb9e-4c9f-af5a-fe836e40ddd1
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a05263ae45df61c47a3580d474863c8d4ff3dd1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637405"
---
# <a name="every-method-array-javascript"></a>every (Método, Array de JavaScript)
Determina si todos los miembros de una matriz satisfacen la prueba especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
array1.every(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Definición|  
|---------------|----------------|  
|`array1`|Obligatorio. Objeto de matriz.|  
|`callbackfn`|Obligatorio. Función que acepta un máximo de tres argumentos. El `every` llamadas al método el `callbackfn` función para cada elemento de `array1` hasta que el `callbackfn` devuelve `false`, o hasta el final de la matriz.|  
|`thisArg`|Opcional. Objeto al que puede hacer referencia la palabra clave `this` en la función `callbackfn`. Si se omite `thisArg`, se usa `undefined` como valor `this`.|  
  
## <a name="return-value"></a>Valor devuelto  
 `true`Si el `callbackfn` función devuelve `true` para toda la matriz elementos; en caso contrario, `false`. Si la matriz no tiene elementos, la `every` método `true`.  
  
## <a name="exceptions"></a>Excepciones  
 Si el argumento `callbackfn` no es un objeto de función, se produce una excepción `TypeError`.  
  
## <a name="remarks"></a>Comentarios  
 El `every` llamadas al método el `callbackfn` funcionar una vez por cada elemento de matriz, en orden ascendente de index, hasta que el `callbackfn` función devuelve `false`. Si un elemento que hace que `callbackfn` para devolver `false` se encuentra, el `every` método vuelve inmediatamente `false`. En caso contrario, el `every` método `true`.  
  
 Para los elementos que faltan en la matriz, no se llama a la función de devolución de llamada.  
  
 Además de los objetos Array, cualquier objeto que tenga una propiedad `every` y que tenga nombres de propiedad indizados numéricamente puede usar el método `length`.  
  
> [!NOTE]
>  Puede usar el [algunos (método, Array)](../../javascript/reference/some-method-array-javascript.md) para comprobar si la función de devolución de llamada devuelve `true` para cualquier elemento de una matriz.  
  
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
  
 En la tabla siguiente se describen los resultados de modificar el objeto Array después de que se inicie el método `every`.  
  
|Condición después del inicio del método `every`|¿Se pasó el elemento a la función de devolución de llamada?|  
|-----------------------------------------------|------------------------------------------|  
|El elemento se agrega más allá de la longitud original de la matriz.|No.|  
|El elemento se agrega para rellenar un elemento que falta en la matriz.|Sí, si ese índice todavía no se pasó a la función de devolución de llamada.|  
|Se cambia el elemento.|Sí, si ese elemento todavía no se pasó a la función de devolución de llamada.|  
|El elemento se elimina de la matriz.|No, a menos que el elemento se haya pasado ya a la función de devolución de llamada.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `every`.  
  
```JavaScript  
// Define the callback function.  
function CheckIfEven(value, index, ar) {  
    document.write(value + " ");  
  
    if (value % 2 == 0)  
        return true;  
    else  
        return false;  
}  
  
// Create an array.  
var numbers = [2, 4, 5, 6, 8];  
  
// Check whether the callback function returns true for all of the  
// array values.  
if (numbers.every(CheckIfEven))  
    document.write("All are even.");  
else  
    document.write("Some are not even.");  
  
// Output:  
// 2 4 5 Some are not even.  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso del argumento `thisArg`, que especifica un objeto al que puede hacer referencia la palabra clave `this`.  
  
```JavaScript  
// Create a function that returns true if the value is  
// numeric and within range.  
var checkNumericRange = function(value) {  
    if (typeof value !== 'number')  
        return false;  
    else   
        return value >= this.minimum && value <= this.maximum;  
}  
  
// Create an array of numbers.  
var numbers = [10, 15, 19];  
  
// Check whether the callback function returns true for  
// all of the array values.  
// The obj argument enables use of the this value  
// within the callback function.  
  
var obj = { minimum: 10, maximum: 20 }  
  
if (numbers.every(checkNumericRange, obj))  
    document.write ("All are within range.");  
else  
    document.write ("Some are not within range.");  
  
// Output:  
//   All are within range.  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Algunos (método, Array)](../../javascript/reference/some-method-array-javascript.md)   
 [filtrar (método, Array)](../../javascript/reference/filter-method-array-javascript.md)   
 [Array (objeto)](../../javascript/reference/array-object-javascript.md)   
 [Uso de matrices](../../javascript/advanced/using-arrays-javascript.md)