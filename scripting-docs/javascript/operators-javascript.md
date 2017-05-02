---
title: "Operadores (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "JavaScript, operadores"
ms.assetid: b8602b69-aba9-46e8-86e1-cb533ad41410
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Operadores (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] tiene un amplio conjunto de operadores, entre los que se incluyen operadores aritméticos, lógicos, bit a bit y de asignación, así como algunos operadores varios.  Para explicaciones y ejemplos, vea los temas acerca de operadores específicos.  
  
## Operadores de cálculo  
  
|Descripción|Símbolo|  
|-----------------|-------------|  
|[Negación unaria](../javascript/reference/subtraction-operator-decrement-javascript.md)|\-|  
|[Increment](../javascript/reference/increment-and-decrement-operators-javascript.md)|\+\+|  
|[Decrement](../javascript/reference/increment-and-decrement-operators-javascript.md)|\-\-|  
|[Multiplicación](../javascript/reference/multiplication-operator-decrement-javascript.md)|\*|  
|[División](../javascript/reference/division-operator-decrement-javascript.md)|\/|  
|[Módulo aritmético](../javascript/reference/modulus-operator-decrementjavascript.md)|%|  
|[Adición](../javascript/reference/addition-operator-decrement-javascript.md)|\+|  
|[Resta](../javascript/reference/subtraction-operator-decrement-javascript.md)|\-|  
  
## Operadores lógicos  
  
|Descripción|Símbolo|  
|-----------------|-------------|  
|[NOT lógico](../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)|\!|  
|[Menor que](../javascript/reference/comparison-operators-javascript.md)|\<|  
|[Mayor que](../javascript/reference/comparison-operators-javascript.md)|\>|  
|[Menor o igual que](../javascript/reference/comparison-operators-javascript.md)|\<\=|  
|[Mayor o igual que](../javascript/reference/comparison-operators-javascript.md)|\>\=|  
|[Igualdad](../javascript/reference/comparison-operators-javascript.md)|\=\=|  
|[Desigualdad](../javascript/reference/comparison-operators-javascript.md)|\!\=|  
|[AND lógico](../javascript/reference/logical-and-operator-decrement-javascript.md)|&&|  
|[OR lógico](../javascript/reference/logical-or-operator-decrement-javascript.md)|&#124;&#124;|  
|[Operador ternario condicional](../javascript/reference/conditional-ternary-operator-decrement-javascript.md)|?:|  
|[Coma](../javascript/reference/comma-operator-decrement-javascript.md)|,|  
|[Igualdad estricta](../javascript/reference/comparison-operators-javascript.md)|\=\=\=|  
|[Desigualdad estricta](../javascript/reference/comparison-operators-javascript.md)|\!\=\=|  
  
## Operadores bit a bit  
  
|Descripción|Símbolo|  
|-----------------|-------------|  
|[NOT bit a bit](../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)|~|  
|[Desplazamiento a la izquierda bit a bit](../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)|\<\<|  
|[Desplazamiento a la derecha bit a bit](../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)|\>\>|  
|[Desplazamiento a la derecha sin signo](../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)|\>\>\>|  
|[AND bit a bit](../javascript/reference/bitwise-and-operator-decrement-javascript.md)|&|  
|[XOR bit a bit](../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)|^|  
|[OR bit a bit](../javascript/reference/bitwise-or-operator-decrement-javascript.md)|&#124;|  
  
## Operadores de asignación  
  
|Descripción|Símbolo|  
|-----------------|-------------|  
|[Asignación](../javascript/reference/assignment-operator-decrement-equal-javascript.md)|\=|  
|[Asignación compuesta](../javascript/reference/compound-assignment-operators-javascript.md)|*OP*\= \(como \+\= y &\=\)|  
  
## Operadores varios  
  
|Descripción|Símbolo|  
|-----------------|-------------|  
|[eliminar](../javascript/reference/delete-operator-decrementjavascript.md)|eliminar|  
|[typeof](../javascript/reference/typeof-operator-decrementjavascript.md)|typeof|  
|[void](../javascript/reference/void-operator-decrementjavascript.md)|void|  
|[instanceof](../javascript/reference/instanceof-operator-decrementjavascript.md)|instanceof|  
|[new](../javascript/reference/new-operator-decrementjavascript.md)|new|  
|[in](../javascript/reference/in-operator-decrementjavascript.md)|in|  
  
## Igualdad e igualdad estricta  
 La diferencia entre \=\= \(igualdad\) y \=\=\= \(igualdad estricta\) es que el operador de igualdad convertirá los valores de distintos tipos antes de comprobar la igualdad.  Por ejemplo, el resultado de comparar la cadena "1" con el número 1 es true.  El operador de igualdad estricta, por otra parte, no convertirá los valores a tipos diferentes, por lo que la cadena "1" y el número 1 no se comparan como iguales.  
  
 Las cadenas primitivas, los números y los valores booleanos se comparan por valor.  Si tienen el mismo valor, son iguales.  Los objetos \(incluidos los objetos `Array`, `Function`, `String`, **Number**, `Boolean`, **Error** `Date` y `RegExp`\) se comparan por referencia.  Aunque dos variables de estos tipos tengan el mismo valor, son iguales solo si hacen referencia exactamente al mismo objeto.  
  
 Por ejemplo:  
  
```javascript  
// Two strings with the same value.  
var string1 = "Hello";  
var string2 = "Hello";  
  
// Two String objects with the same value.  
var StringObject1 = new String(string1);  
var StringObject2 = new String(string2);  
  
if (string1 == string2)  
    document.write("string1 is equal to string2 <br/>");  
  
if (StringObject1 != StringObject2)  
    document.write("StringObject1 is not equal to StringObject2 <br/>");  
  
// To compare the values of String objects, use the toString() or valueOf() methods.  
if (StringObject1.valueOf() == StringObject2.valueOf())  
    document.write("The value of StringObject1 is equal to the value of StringObject2");  
  
//Output:  
// string1 is equal to string2   
// StringObject1 is not equal to StringObject2   
// The value of StringObject1 is equal to the value of StringObject2  
  
```