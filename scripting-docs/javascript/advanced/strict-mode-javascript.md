---
title: Modo strict (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1038
- VS.WebClient.Help.SCRIPT1050
- VS.WebClient.Help.SCRIPT1042
- VS.WebClient.Help.SCRIPT1041
- VS.WebClient.Help.SCRIPT1046
- VS.WebClient.Help.SCRIPT1045
- VS.WebClient.Help.SCRIPT1037
- VS.WebClient.Help.SCRIPT1039
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strict mode
- use strict
ms.assetid: 0f27022a-f41c-4504-965c-5a2701f342cd
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77ee7d54dd265026b2bf4c9af52a71cccf9a7675
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569575"
---
# <a name="strict-mode-javascript"></a>Strict (Modo de JavaScript)
El modo strict es una manera de introducir una mejor comprobación de errores en el código. Cuando se utiliza el modo strict, no se puede, por ejemplo, usar variables declaradas de forma implícita, asignar un valor a una propiedad de solo lectura o agregar una propiedad a un objeto que no es extensible. Las restricciones se indican en la sección [Restricciones del código en modo strict](../../javascript/advanced/strict-mode-javascript.md#rest), más adelante en este tema. Para obtener más información sobre el modo strict, consulte [ECMAScript Language Specification, 5th edition](http://www.ecma-international.org/publications/standards/Ecma-262.htm) (Especificación del lenguaje ECMAScript, Quinta edición).  
  
> [!WARNING]
>  El modo strict no se admite en las versiones de Internet Explorer anteriores a Internet Explorer 10.  
  
## <a name="declaring-strict-mode"></a>Declarar el modo strict  
 Puedes declarar el modo strict agregando `"use strict";` al principio de un archivo, un programa o una función. Este tipo de declaración se conoce como *prólogo de directivas*. El ámbito de una declaración de modo strict depende del contexto. Si se declara en un contexto global (fuera del ámbito de una función), todo el código del programa está en modo strict. Si se declara en una función, todo el código de la función está en modo strict. Por ejemplo, en el siguiente ejemplo todo el código está en modo strict y la declaración de variables fuera de la función produce el error de sintaxis "Variable sin definir en modo strict".  
  
```JavaScript  
"use strict";  
function testFunction(){  
    var testvar = 4;  
    return testvar;  
}  
  
// This causes a syntax error.  
testvar = 5;  
  
```  
  
 En el ejemplo siguiente, solo el código contenido en `testFunction` está en modo strict. La declaración de variables fuera de la función no produce un error de sintaxis, pero la declaración dentro de la función, sí.  
  
```JavaScript  
function testFunction(){  
    "use strict";  
    // This causes a syntax error.  
    testvar = 4;  
    return testvar;  
}  
testvar = 5;  
  
```  
  
<a name="rest"></a>   
## <a name="restrictions-on-code-in-strict-mode"></a>Restricciones del código en modo strict  
 En la tabla siguiente se indican las restricciones más importantes que se aplican en el modo strict.  
  
|||||  
|-|-|-|-|  
|**Elemento del lenguaje**|**Restricción**|**Error**|**Ejemplo**|  
|Variable|Usar una variable sin declararla.|SCRIPT5042: Variable sin definir en modo strict|`testvar = 4;`|  
|Propiedad de solo lectura|Escribir en una propiedad de solo lectura.|SCRIPT5045: No se permite la asignación a propiedades de solo lectura en modo strict|`var testObj = Object.defineProperties({}, {     prop1: {         value: 10,         writable: false // by default     },     prop2: {         get: function () {         }     } }); testObj.prop1 = 20;  testObj.prop2 = 30;`|  
|Propiedad no extensible|Agregar una propiedad a un objeto cuyo atributo `extensible` está establecido en `false`.|SCRIPT5046: No se puede crear ninguna propiedad para un objeto no extensible|`var testObj = new Object();  Object.preventExtensions(testObj);  testObj.name = "Bob";`|  
|`delete`|Eliminar una variable, una función o un argumento.<br /><br /> Eliminar una propiedad cuyo atributo `configurable` está establecido en `false`.|SCRIPT1045: No se permite llamar a delete en la \<expresión> en modo strict|`var testvar = 15; function testFunc() {}; delete testvar; delete testFunc;  Object.defineProperty(testObj, "testvar", {     value: 10,     configurable: false     }); delete testObj.testvar;`|  
|Duplicar una propiedad|Definir una propiedad más de una vez en un literal de objeto.|SCRIPT1046: No se permiten varias definiciones de una propiedad en modo strict|`var testObj = {     prop1: 10,     prop2: 15,     prop1: 20 };`|  
|Duplicar un nombre de parámetro|Usar un nombre de parámetro más de una vez en una función.|SCRIPT1038: No se permiten nombres de parámetros formales duplicados en modo strict|`function testFunc(param1, param1) {     return 1; };`|  
|Palabras clave reservadas para uso futuro|Usar una palabra clave reservada para uso futuro como variable o nombre de función.|SCRIPT1050: El uso de una palabra reservada para uso futuro para un identificador no es válido. El nombre del identificador está reservado en modo strict.|-                      `implements`<br /><br /> -                      `interface`<br /><br /> -                      `package`<br /><br /> -                      `private`<br /><br /> -                      `protected`<br /><br /> -                      `public`<br /><br /> -                      `static`<br /><br /> -                      `yield`|  
|Octales|Asignar un valor octal a un literal numérico o intentar usar un carácter de escape en un valor octal.|SCRIPT1039: No se permiten literales numéricos octales y caracteres de escape en modo strict|`var testoctal = 010; var testescape = \010;`|  
|`this`|El valor de `this` no se convierte al objeto global cuando es `null` o `undefined`.||`function testFunc() {     return this; } var testvar = testFunc();`<br /><br /> En modo no strict, el valor de `testvar` es el objeto global, pero en modo strict su valor es `undefined`.|  
|`eval` como identificador|La cadena "eval" no se puede usar como identificador (nombre de variable o función, nombre de parámetro, etc.).||`var eval = 10;`|  
|Función declarada dentro de una instrucción o un bloque|No se puede declarar una función dentro de una instrucción o un bloque.|SCRIPT1047: En modo strict, las declaraciones de función no pueden estar anidadas dentro de una instrucción o bloque. Solo pueden aparecer en el nivel superior o directamente dentro del cuerpo de una función.|`var arr = [1, 2, 3, 4, 5]; var index = null; for (index in arr) {     function myFunc() {}; }`|  
|Variable declarada dentro de una función `eval`|Si una variable se declara dentro de una función `eval`, no se puede usar fuera de esa función.|SCRIPT1041: Uso no válido de 'eval' en modo strict|`eval("var testvar = 10"); testvar = 15;`<br /><br /> Es posible la evaluación indirecta, pero igualmente no es posible usar una variable declarada fuera de la función `eval`.<br /><br /> `var indirectEval = eval; indirectEval("var testvar = 10;"); document.write(testVar);`<br /><br /> Este código produce un error SCRIPT5009: 'testVar' no está definido.|  
|`Arguments` como identificador|La cadena "arguments" no se puede usar como identificador (nombre de variable o función, nombre de parámetro, etc.).|SCRIPT1042: Uso no válido de 'arguments' en modo strict|`var arguments = 10;`|  
|`arguments` dentro de una función|No puede cambiar los valores de los miembros del objeto `arguments` local.||`function testArgs(oneArg) {     arguments[0] = 20; }`<br /><br /> En modo no strict, puede cambiar el valor del parámetro `oneArg` modificando el valor de `arguments[0]`, de tal forma que el valor de `oneArg` y de `arguments[0]` sea 20. En modo strict, cambiar el valor de `arguments[0]` no afecta al valor de `oneArg`, porque el objeto `arguments` no es más que una copia local.|  
|`arguments.callee`|No permitido.||`function (testInt) {     if (testInt-- == 0)         return;     arguments.callee(testInt--); }`|  
|`with`|No permitido.|SCRIPT1037: No se permiten instrucciones 'with' en modo strict|`with (Math){     x = cos(3);     y = tan(7); }`|