---
title: Operadores (JavaScript) | Microsoft Docs
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
helpviewer_keywords: JavaScript, operators
ms.assetid: b8602b69-aba9-46e8-86e1-cb533ad41410
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9d0a098418399dba19b77a12c057a3fba334e31
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="operators-javascript"></a>Operadores (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] tiene un rango completo de operadores, incluidos los operadores aritméticos, lógicos, bit a bit, de asignación y algunos operadores variados. Para obtener explicaciones y ejemplos, vea los temas sobre los operadores concretos.  
  
## <a name="computational-operators"></a>Operadores de cálculo  
  
|Descripción|Símbolo|  
|-----------------|------------|  
|[Negación unaria](../javascript/reference/subtraction-operator-decrement-javascript.md)|-|  
|[Incremento](../javascript/reference/increment-and-decrement-operators-javascript.md)|++|  
|[Decremento](../javascript/reference/increment-and-decrement-operators-javascript.md)|--|  
|[Multiplicación](../javascript/reference/multiplication-operator-decrement-javascript.md)|*|  
|[División](../javascript/reference/division-operator-decrement-javascript.md)|/|  
|[Modulus aritmético](../javascript/reference/modulus-operator-decrementjavascript.md)|%|  
|[Suma](../javascript/reference/addition-operator-decrement-javascript.md)|+|  
|[Resta](../javascript/reference/subtraction-operator-decrement-javascript.md)|-|  
  
## <a name="logical-operators"></a>Operadores lógicos  
  
|Descripción|Símbolo|  
|-----------------|------------|  
|[NOT lógico](../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)|!|  
|[Menor que](../javascript/reference/comparison-operators-javascript.md)|\<|  
|[Mayor que](../javascript/reference/comparison-operators-javascript.md)|>|  
|[Menor o igual que](../javascript/reference/comparison-operators-javascript.md)|\<=|  
|[Mayor o igual que](../javascript/reference/comparison-operators-javascript.md)|>=|  
|[Igualdad](../javascript/reference/comparison-operators-javascript.md)|==|  
|[Desigualdad](../javascript/reference/comparison-operators-javascript.md)|!=|  
|[AND lógico](../javascript/reference/logical-and-operator-decrement-javascript.md)|&&|  
|[OR lógico](../javascript/reference/logical-or-operator-decrement-javascript.md)|&#124;&#124;|  
|[Condicional (ternario)](../javascript/reference/conditional-ternary-operator-decrement-javascript.md)|?:|  
|[Coma](../javascript/reference/comma-operator-decrement-javascript.md)|,|  
|[Igualdad estricta](../javascript/reference/comparison-operators-javascript.md)|===|  
|[Desigualdad estricta](../javascript/reference/comparison-operators-javascript.md)|!==|  
  
## <a name="bitwise-operators"></a>Operadores bit a bit  
  
|Descripción|Símbolo|  
|-----------------|------------|  
|[NOT bit a bit](../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)|~|  
|[Desplazamiento a la izquierda bit a bit](../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)|<\<|  
|[Desplazamiento a la derecha bit a bit](../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)|>>|  
|[Desplazamiento a la derecha sin signo](../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)|>>>|  
|[AND bit a bit](../javascript/reference/bitwise-and-operator-decrement-javascript.md)|&|  
|[XOR bit a bit](../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)|^|  
|[OR bit a bit](../javascript/reference/bitwise-or-operator-decrement-javascript.md)|&#124;|  
  
## <a name="assignment-operators"></a>Operadores de asignación  
  
|Descripción|Símbolo|  
|-----------------|------------|  
|[Asignación](../javascript/reference/assignment-operator-decrement-equal-javascript.md)|=|  
|[Asignación compuesta](../javascript/reference/compound-assignment-operators-javascript.md)|*OP*= (como += y &=)|  
  
## <a name="miscellaneous-operators"></a>Operadores varios  
  
|Descripción|Símbolo|  
|-----------------|------------|  
|[delete](../javascript/reference/delete-operator-decrementjavascript.md)|eliminar|  
|[typeof](../javascript/reference/typeof-operator-decrementjavascript.md)|typeof|  
|[void](../javascript/reference/void-operator-decrementjavascript.md)|void|  
|[instanceof](../javascript/reference/instanceof-operator-decrementjavascript.md)|instanceof|  
|[new](../javascript/reference/new-operator-decrementjavascript.md)|new|  
|[in](../javascript/reference/in-operator-decrementjavascript.md)|en|  
  
## <a name="equality-and-strict-equality"></a>Igualdad e igualdad estricta  
 La diferencia entre == (igualdad) e === (igualdad estricta) es que el operador de igualdad convertirá los valores de distintos tipos antes de comprobar la igualdad. Por ejemplo, si se compara la cadena "1" con el número 1, se considerará true. El operador de igualdad estricta, por otro lado, no convertirá los valores de tipos diferentes y, por tanto, la cadena "1" no se considerará igual al número 1.  
  
 Los booleanos, números y cadenas primitivos se comparan por valor. Si tienen el mismo valor, son iguales. Los objetos (incluidos los objetos `Array`, `Function`, `String`, **Number**, `Boolean`, **Error**, `Date` y `RegExp`) se comparan por referencia. Incluso si dos variables de estos tipos tienen el mismo valor, solo son iguales si hacen referencia exactamente al mismo objeto.  
  
 Por ejemplo:  
  
```JavaScript  
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