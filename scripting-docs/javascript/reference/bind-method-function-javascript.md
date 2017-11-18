---
title: "Bind (método) (función) (JavaScript) | Documentos de Microsoft"
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
- parameters [JavaScript], bind method
- arguments [JavaScript], bind method
- bind method [JavaScript]
- this keyword [JavaScript], bind method
ms.assetid: 28946f47-b758-48cf-b508-610a0f2f6e19
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd7fc752df9bd41f8625ac2cb484486dfd19558d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="bind-method-function-javascript"></a>bind (Método, Function de JavaScript)
Para una función determinada, crea una función enlazada con el mismo cuerpo que la función original. En la función enlazada, el objeto `this` se resuelve en el objeto pasado. La función enlazada tiene los parámetros iniciales especificados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
function.bind(thisArg[,arg1[,arg2[,argN]]])  
```  
  
#### <a name="parameters"></a>Parámetros  
 `function`  
 Obligatorio. Objeto de función.  
  
 `thisArg`  
 Obligatorio. Objeto al que se puede hacer referencia dentro de la nueva función, mediante la palabra clave `this`.  
  
 `arg1`[,`arg2`[,`argN`]]]  
 Opcional. Lista de argumentos que se pasarán a la nueva función.  
  
## <a name="return-value"></a>Valor devuelto  
 Nueva función que es igual que la función `function`, excepto el objeto `thisArg` y los argumentos iniciales.  
  
## <a name="exceptions"></a>Excepciones  
 Si el parámetro `function` especificado no es una función, se produce una excepción `TypeError`.  
  
## <a name="example"></a>Ejemplo  
 En el código siguiente se muestra cómo puede utilizar el método `bind`.  
  
```JavaScript  
// Define the original function.  
var checkNumericRange = function (value) {  
    if (typeof value !== 'number')  
        return false;  
    else  
        return value >= this.minimum && value <= this.maximum;  
}  
  
// The range object will become the this value in the callback function.  
var range = { minimum: 10, maximum: 20 };  
  
// Bind the checkNumericRange function.  
var boundCheckNumericRange = checkNumericRange.bind(range);  
  
// Use the new function to check whether 12 is in the numeric range.  
var result = boundCheckNumericRange (12);  
document.write(result);  
  
// Output: true  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, el objeto `thisArg` es diferente del objeto que contiene el método original.  
  
```JavaScript  
// Create an object that contains the original function.  
var originalObject = {  
    minimum: 50,  
    maximum: 100,  
    checkNumericRange: function (value) {  
        if (typeof value !== 'number')  
            return false;  
        else  
            return value >= this.minimum && value <= this.maximum;  
    }  
}  
  
// Check whether 10 is in the numeric range.  
var result = originalObject.checkNumericRange(10);  
document.write(result + " ");  
// Output: false  
  
// The range object supplies the range for the bound function.  
var range = { minimum: 10, maximum: 20 };  
  
// Create a new version of the checkNumericRange function that uses range.  
var boundObjectWithRange = originalObject.checkNumericRange.bind(range);  
  
// Check whether 10 is in the numeric range.  
var result = boundObjectWithRange(10);  
document.write(result);  
// Output: true  
```  
  
## <a name="example"></a>Ejemplo  
 En el código siguiente se muestra cómo utilizar los argumentos `arg1[,arg2[,argN]]]`. La función enlazada utiliza los parámetros especificados en el método `bind` como primer y segundo parámetros. Todos los parámetros especificados cuando se llama a la función enlazada se utilizan como el tercer o cuarto parámetro (y así sucesivamente).  
  
```JavaScript  
// Define the original function with four parameters.  
var displayArgs = function (val1, val2, val3, val4) {  
    document.write(val1 + " " + val2 + " " + val3 + " " + val4);  
}  
  
var emptyObject = {};  
  
// Create a new function that uses the 12 and "a" parameters  
// as the first and second parameters.  
var displayArgs2 = displayArgs.bind(emptyObject, 12, "a");  
  
// Call the new function. The "b" and "c" parameters are used  
// as the third and fourth parameters.  
displayArgs2("b", "c");  
// Output: 12 a b c   
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Objeto de función](../../javascript/reference/function-object-javascript.md)   
 [filtrar (método, Array)](../../javascript/reference/filter-method-array-javascript.md)   
 [Utilizar el método bind](../../javascript/advanced/using-the-bind-method-javascript.md)   
 [Aplicación de ejemplo de JavaScript de hilo (tienda Windows)](http://hilojs.codeplex.com/SourceControl/latest)