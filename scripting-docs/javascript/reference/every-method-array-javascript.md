---
title: "every (M&#233;todo, Array de JavaScript) | Microsoft Docs"
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
  - "matrices [JavaScript], every (método)"
  - "every (método)"
ms.assetid: dc4ee2f8-fb9e-4c9f-af5a-fe836e40ddd1
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# every (M&#233;todo, Array de JavaScript)
Determina si todos los miembros de una matriz satisfacen la prueba especificada.  
  
## Sintaxis  
  
```  
  
array1.every(callbackfn[, thisArg])  
```  
  
#### Parámetros  
  
|Parámetro|Definición|  
|---------------|----------------|  
|`array1`|Obligatorio.  Objeto de matriz.|  
|`callbackfn`|Obligatorio.  Función que acepta un máximo de tres argumentos.  El método `every` llama a la función `callbackfn` para cada elemento de `array1` hasta que `callbackfn` devuelve `false` o hasta el final de la matriz.|  
|`thisArg`|Opcional.  Objeto al que puede hacer referencia la palabra clave `this` en la función `callbackfn`.  Si se omite `thisArg`, se usa `undefined` como valor de `this`.|  
  
## Valor devuelto  
 Es `true` si la función `callbackfn` devuelve `true` para todos los elementos de la matriz; de lo contrario, es `false`.  Si la matriz no tiene ningún elemento, el método `every` devuelve `true`.  
  
## Excepciones  
 Si el argumento `callbackfn` no es un objeto de función, se produce una excepción `TypeError`.  
  
## Comentarios  
 El método `every` llama a la función `callbackfn` una vez para cada elemento de matriz, en orden de índice ascendente, hasta que la función `callbackfn` devuelve `false`.  Si se encuentra un elemento que hace que `callbackfn` devuelva `false`, el método `every` devuelve inmediatamente `false`.  De lo contrario, el método `every` devuelve `true`.  
  
 Para los elementos que faltan en la matriz, no se llama a la función de devolución de llamada.  
  
 Además de los objetos Array, cualquier objeto que tenga una propiedad `length` y que tenga nombres de propiedad indizados numéricamente puede usar el método `every`.  
  
> [!NOTE]
>  Puedes usar [some \(Método, Array\)](../../javascript/reference/some-method-array-javascript.md) para comprobar si la función de devolución de llamada devuelve `true` para cualquier elemento de una matriz.  
  
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
  
 En la tabla siguiente se describen los resultados de modificar el objeto Array después de que se inicie el método `every`.  
  
|Condición después del inicio del método `every`|¿Se pasó el elemento a la función de devolución de llamada?|  
|-----------------------------------------------------|-----------------------------------------------------------------|  
|El elemento se agrega más allá de la longitud original de la matriz.|No.|  
|El elemento se agrega para rellenar un elemento que falta en la matriz.|Sí, si ese índice todavía no se pasó a la función de devolución de llamada.|  
|Se cambia el elemento.|Sí, si ese elemento todavía no se pasó a la función de devolución de llamada.|  
|El elemento se elimina de la matriz.|No, a menos que el elemento se haya pasado ya a la función de devolución de llamada.|  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `every`.  
  
```javascript  
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
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del argumento `thisArg`, que especifica un objeto al que puede hacer referencia la palabra clave `this`.  
  
```javascript  
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
  
## Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vea también  
 [some \(Método, Array\)](../../javascript/reference/some-method-array-javascript.md)   
 [filter \(Método, Array\)](../../javascript/reference/filter-method-array-javascript.md)   
 [Array \(Objeto\)](../../javascript/reference/array-object-javascript.md)   
 [Utilizar matrices](../../javascript/advanced/using-arrays-javascript.md)