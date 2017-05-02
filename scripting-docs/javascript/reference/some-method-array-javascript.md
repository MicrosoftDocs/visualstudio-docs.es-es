---
title: "some (M&#233;todo, Array de JavaScript) | Microsoft Docs"
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
  - "matrices [JavaScript], some (método)"
  - "some (método) [JavaScript]"
ms.assetid: 7b6822f9-c406-4f4e-bfec-a93459745992
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# some (M&#233;todo, Array de JavaScript)
Determina si la función de devolución de llamada especificada devuelve `true` para cualquier elemento de una matriz.  
  
## Sintaxis  
  
```  
  
array1.some(callbackfn[, thisArg])  
```  
  
#### Parámetros  
  
|Parámetro|Definición|  
|---------------|----------------|  
|`array1`|Obligatorio.  Objeto de matriz.|  
|`callbackfn`|Obligatorio.  Función que acepta un máximo de tres argumentos.  El método `some` llama a la función `callbackfn` para cada elemento de `array1` hasta que `callbackfn` devuelve `true` o hasta el final de la matriz.|  
|`thisArg`|Opcional.  Objeto al que puede hacer referencia la palabra clave `this` en la función `callbackfn`.  Si se omite `thisArg`, se usa `undefined` como valor de `this`.|  
  
## Valor devuelto  
 Es `true` si la función `callbackfn` devuelve `true` para cualquier elemento de la matriz; de lo contrario, es `false`.  
  
## Excepciones  
 Si el argumento `callbackfn` no es un objeto de función, se produce una excepción `TypeError`.  
  
## Comentarios  
 El método `some` llama a la función `callbackfn` en cada elemento de matriz, en orden de índice ascendente, hasta que la función `callbackfn` devuelve `true`.  Si se encuentra un elemento que hace que `callbackfn` devuelva `true`, el método `some` devuelve inmediatamente `true`.  Si la devolución de llamada no devuelve `true` en ningún elemento, el método `some` devuelve `false`.  
  
 Para los elementos que faltan en la matriz, no se llama a la función de devolución de llamada.  
  
 Además de los objetos Array, cualquier objeto que tenga una propiedad `length` y que tenga nombres de propiedad indizados numéricamente puede usar el método `some`.  
  
> [!NOTE]
>  Puedes usar [every \(Método, Array\)](../../javascript/reference/every-method-array-javascript.md) para comprobar si la función de devolución de llamada devuelve `true` para todos los elementos de una matriz.  
  
## Sintaxis de la función de devolución de llamada  
 La sintaxis de la función de devolución de llamada es la siguiente:  
  
 `function callbackfn(value, index, array1)`  
  
 Puedes declarar la función de devolución de llamada con hasta tres parámetros.  
  
 En la tabla siguiente se muestran los parámetros de la función de devolución de llamada.  
  
|Parámetro de devolución de llamada|Definición|  
|----------------------------------------|----------------|  
|`value`|Valor del elemento de la matriz.|  
|`index`|Índice numérico del elemento de la matriz.|  
|`array1`|Objeto Array que contiene el elemento.|  
  
## Modificar el objeto Array  
 La función de devolución de llamada puede modificar el objeto Array.  
  
 En la tabla siguiente se describen los resultados de modificar el objeto Array después de que se inicie el método `some`.  
  
|Condición después del inicio del método `some`|¿Se pasó el elemento a la función de devolución de llamada?|  
|----------------------------------------------------|-----------------------------------------------------------------|  
|El elemento se agrega más allá de la longitud original de la matriz.|No.|  
|El elemento se agrega para rellenar un elemento que falta en la matriz.|Sí, si ese índice todavía no se pasó a la función de devolución de llamada.|  
|Se cambia el elemento.|Sí, si ese elemento todavía no se pasó a la función de devolución de llamada.|  
|El elemento se elimina de la matriz.|No, a menos que el elemento se haya pasado ya a la función de devolución de llamada.|  
  
## Ejemplo  
 En el ejemplo siguiente se usa el método `some` para averiguar si algunos elementos de una matriz son pares.  
  
```javascript  
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
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo usar el parámetro `thisArg`, que especifica un objeto al que la palabra clave `this` puede hacer referencia.  Comprueba si cualquiera de los números de una matriz está fuera del intervalo proporcionado por un objeto pasado.  
  
```javascript  
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
  
## Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vea también  
 [every \(Método, Array\)](../../javascript/reference/every-method-array-javascript.md)   
 [filter \(Método, Array\)](../../javascript/reference/filter-method-array-javascript.md)   
 [map \(Método, Array\)](../../javascript/reference/map-method-array-javascript.md)