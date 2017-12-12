---
title: Funciones (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: intrinsic JavaScript functions
ms.assetid: e2a72b5a-3edd-43d8-95e8-91721b38c1c1
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fd5626af6417b5f0010545874bd15c86b30a303a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="functions-javascript"></a>Funciones (JavaScript)
Las funciones [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] realizan acciones y también pueden devolver valores. A veces son los resultados de cálculos o comparaciones. Las funciones también se denominan "métodos globales".  
  
 Las funciones combinan varias operaciones en un nombre. Esto le permite simplificar el código. Puede escribir un conjunto de instrucciones, asignarle un nombre y, a continuación, ejecutar todo el conjunto llamándolo y pasándole la información que necesita.  
  
 Para pasar información a una función, escriba la información entre paréntesis después del nombre de la función. La información que se pasa a una función se denomina argumento o parámetro. Algunas funciones no aceptan ningún argumento, mientras que otras usan uno o varios argumentos. En algunas funciones, el número de argumentos depende de cómo se usa la función.  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] admite dos tipos de funciones: las que están integradas en el lenguaje y las que crea usted mismo.  
  
## <a name="built-in-functions"></a>Funciones integradas  
 El lenguaje [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] incluye varias funciones integradas. Algunas permiten controlar expresiones y caracteres especiales, mientras que otras convierten cadenas en valores numéricos.  
  
 Vea [Métodos de JavaScript](../javascript/reference/javascript-methods.md) para obtener información sobre estas funciones integradas.  
  
## <a name="creating-your-own-functions"></a>Crear sus propias funciones  
 Puede crear sus propias funciones y usarlas cuando sea necesario. Una definición de función consta de una instrucción function y un bloque de instrucciones de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
 La función **checkTriplet** del ejemplo siguiente toma como argumentos las longitudes de los lados de un triángulo. A partir de ellos calcula si el triángulo es un triángulo rectángulo comprobando si los tres números constituyen una terna pitagórica (el cuadrado de la longitud de la hipotenusa de un triángulo rectángulo es igual a la suma de los cuadrados de las longitudes de los dos catetos). La función checkTriplet llama a una de otras dos funciones para realizar la prueba real.  
  
 Observe el uso de un número muy pequeño ("epsilon") como variable de prueba en la versión de punto flotante de la prueba. Debido a las incertidumbres y los errores de redondeo en los cálculos de punto flotante, no resulta práctico probar directamente si los tres números constituyen una terna pitagórica, a menos que se sepa que los tres valores en cuestión son números enteros. Dado que la prueba directa es más precisa, el código de este ejemplo determina si es apropiada y, en caso de que lo sea, la usa.  
  
```JavaScript  
var epsilon = 0.00000000001; // Some very small number to test against.  
  
// The test function for integers.  
function integerCheck(a, b, c)   
{  
   // The test itself.  
   if ( (a*a) == ((b*b) + (c*c)) )     
      return true;  
  
   return false;  
} // End of the integer checking function.  
  
// The test function for floating-point numbers.  
function floatCheck(a, b, c)     
{  
   // Make the test number.  
   var delta = ((a*a) - ((b*b) + (c*c)))  
  
   // The test requires the absolute value  
   delta = Math.abs(delta);  
  
   // If the difference is less than epsilon, then it's pretty close.  
   if (delta < epsilon)     
      return true;  
  
   return false;  
} // End of the floating-poing check function.  
  
// The triplet checker.   
function checkTriplet(a, b, c)  
{   
   // Create a temporary variable for swapping values  
   var d = 0;   
  
   // First, move the longest side to position "a".  
  
   // Swap a and b if necessary  
   if (b > a)  
   {  
      d = a;  
      a = b;  
      b = d;  
   }  
  
   // Swap a and c if necessary  
   if (c > a)  
   {  
      d = a;  
      a = c;  
      c = d;  
   }  
  
   // Test all 3 values. Are they integers?  
   if (((a % 1) == 0) && ((b % 1) == 0) && ((c % 1) == 0))  
   {   
      // If so, use the precise check.  
      return integerCheck(a, b, c);   
   }  
   else  
   {  
      // If not, get as close as is reasonably possible.  
      return floatCheck(a, b, c);   
   }  
} // End of the triplet check function.  
  
// The next three statements assign sample values for testing purposes.  
var sideA = 5;  
var sideB = 5;  
var sideC = Math.sqrt(50.001);  
  
// Call the function. After the call, 'result' contains the result.  
var result = checkTriplet(sideA, sideB, sideC);  
```  
  
<a name="Arrow"></a>   
## <a name="arrow-functions"></a>Funciones de flecha  
 La sintaxis de la función de flecha, `=>`, proporciona un método abreviado para especificar una función anónima. Esta es la sintaxis de la función de flecha.  
  
```JavaScript  
([arg] [, arg]) => {  
    statements  
}  
```  
  
 Los valores a la izquierda de la flecha, que pueden aparecer entre paréntesis, especifican los argumentos que se pasan a la función. No es necesario usar paréntesis si solo hay un argumento para la función. Los paréntesis son necesarios si no se pasa ningún argumento. La definición de función a la derecha de la flecha puede ser una expresión, como `v + 1`, o un bloque de instrucciones entre llaves ({}).  
  
> [!IMPORTANT]
>  La sintaxis de la función de flecha solo se admite en [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)].  
  
 No se puede usar el operador `new` con una función de flecha.  
  
 En los ejemplos de código siguientes se muestra el uso de la función de flecha con expresiones como definiciones de función. En el primer ejemplo, se pasa v como argumento a la expresión. En el segundo ejemplo, se pasan v e i como argumentos a la expresión.  
  
```  
var evens = [2, 4, 6, 8];  
  
// Using standard syntax.  
var odds = evens.map(function(v) { return v + 1; });  
  
// Using arrow function syntax.  
// Add one to each value to produce output.  
var odds = evens.map(v => v + 1);  
  
// The following line of code adds the index value to the passed  
// in value to produce output.  
// Note: the second argument to the callback function in the map   
// method is the index value (i).  
var nums = evens.map((v, i) => v + i);  
  
console.log(odds);  
console.log(nums);  
  
// Output:  
// [object Array] [3, 5, 7, 9]  
// [object Array] [2, 5, 8, 11]  
```  
  
 En el ejemplo de código siguiente se muestra el uso de la función de flecha con un bloque de instrucciones.  
  
```JavaScript  
var fives = new Array();  
  
// Statement block, re-using nums array from previous example.  
// Note: The first argument to the callback function in forEach  
// is the value of the array element (v).  
nums.forEach(v => {  
  if (v % 5 === 0)  
    fives.push(v);  
});  
  
console.log(fives);  
  
// Output:  
// [object Array] [5]  
```  
  
 A diferencia de las funciones estándar, las funciones de flecha comparten el mismo objeto `this` léxico como código circundante, que puede usarse para eliminar la necesidad de soluciones alternativas, como `var self = this;`.  
  
 En el ejemplo siguiente se muestra que el valor del objeto `this` dentro de la función de flecha es el mismo que en el código circundante (sigue haciendo referencia a la variable `bob`).  
  
```JavaScript  
var bob = {  
  _name: "Bob",  
  _friends: ["Pete", "Joe", "Larry"],  
  printFriends() {  
    this._friends.forEach(f =>  
      console.log(this._name + " knows " + f));  
  }  
}  
  
// Output:  
// Bob knows Pete  
// Bob knows Joe  
// Bob knows Larry  
```  
  
 Las funciones de flecha también comparten el mismo objeto `arguments` léxico como código circundante (igual que el objeto `this`).  
  
<a name="Default"></a>   
## <a name="default-parameters"></a>Parámetros predeterminados  
 Puede especificar un valor predeterminado para un parámetro en una función asignándole un valor inicial. El valor predeterminado puede ser un valor constante o una expresión.  
  
> [!IMPORTANT]
>  Los parámetros predeterminados solo se admiten en [!INCLUDE[jsv12textExp](../javascript/includes/jsv12textexp-md.md)].  
  
 En el ejemplo siguiente, el valor predeterminado de y es 10 y el valor predeterminado de z es 20. La función usará 10 como valor de y, a menos que el llamador pase un valor distinto (o no definido) como segundo argumento. La función usará 20 como valor de z, a menos que el llamador pase un valor distinto (o no definido) como tercer argumento.  
  
```JavaScript  
var val = 20;  
  
function f(x, y=10, z=val) {  
  return x + y + z;  
}  
  
console.log(f(3));  
console.log(f(3, 3));  
console.log(f(3, 3, 3));  
  
// Output:  
// 33  
// 26  
// 9  
```  
  
<a name="Rest"></a>   
## <a name="rest-parameters"></a>Parámetros de REST  
 Los parámetros de REST, especificados mediante el operador de propagación (), permiten activar argumentos consecutivos en una llamada de función a una matriz.  
  
 Los parámetros de REST eliminan la necesidad de usar el objeto `arguments`. Los parámetros de REST se diferencian del objeto `arguments` en varios aspectos, como los siguientes:  
  
-   Un parámetro de REST es una instancia de matriz real y, por tanto, admite operaciones que pueden realizarse en una matriz.  
  
-   Un parámetro de REST incluye solo los argumentos consecutivos que no se pasan como argumentos (con nombre) independientes (en cambio, el objeto `arguments` contiene todos los argumentos pasados a la función).  
  
> [!IMPORTANT]
>  Los parámetros de REST y el operador de propagación solo se admiten en [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)].  
  
 En el ejemplo de código siguiente, se pasan "hello" y true como valores de la matriz y se almacenan en el parámetro y. El parámetro de REST debe ser el último parámetro de la función.  
  
```JavaScript  
function f(x, ...y) {  
  // y is an array.  
  return x * y.length;  
}  
  
console.log(f(3, "hello", true));  
  
// Output:  
// 6  
  
```  
  
 Para conocer otros usos del operador de propagación, vea [Operador Spread](../javascript/reference/spread-operator-decrement-dot-dot-dot-javascript.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia del lenguaje JavaScript](../javascript/javascript-language-reference.md)