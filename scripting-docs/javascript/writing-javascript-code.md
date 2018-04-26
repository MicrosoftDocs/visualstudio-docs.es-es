---
title: Escribir código JavaScript | Microsoft Docs
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
- vs.htmldesigner.html
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- code, JavaScript syntax
- comments, JavaScript code
- JavaScript code
ms.assetid: dde28266-0d0f-4460-a819-f931cf0911ad
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e50bc25f818724b59d9adda51f97d76ae14de2b4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="writing-javascript-code"></a>Escribir código JavaScript
Al igual que muchos otros lenguajes de programación, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] se organiza en instrucciones, bloques que constan de conjuntos relacionados de instrucciones y comentarios. Dentro de una instrucción puede utilizar variables, cadenas, números y expresiones.  
  
## <a name="statements"></a>Instrucciones  
 Un programa [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] es una colección de instrucciones. Las instrucciones [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] combinan expresiones de tal manera que llevan a cabo una tarea completa.  
  
 Una instrucción está formada por una o varias expresiones, palabras clave u operadores (símbolos). Normalmente, una instrucción se escribe en una sola línea, aunque se puede escribir en dos o más. Además, se pueden escribir dos o más instrucciones en la misma línea, separándolas con punto y coma. En general, cada línea nueva comienza una nueva instrucción. Es buena idea terminar las instrucciones de forma explícita. Para ello, utilice el punto y coma (;), que es el carácter de terminación de instrucciones [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
 A continuación se muestran dos ejemplos de instrucciones [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]. Las frases después de los caracteres / / son *comentarios*, que son notas explicativas en el programa.  
  
```JavaScript  
var aBird = "Robin"; // Assign the text "Robin" to the variable aBird.  
var today = new Date(); // Assign today's date to the variable today.  
```  
  
 Un grupo de instrucciones [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] entre llaves ({}) se denomina *bloque*. Por lo general, las instrucciones agrupadas en un bloque pueden tratarse como una sola instrucción. Esto significa que puede utilizar bloques en la mayoría de los sitios en que [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] espera una sola instrucción. Algunas excepciones destacadas son los encabezados de los bucles **for** y `while`. Tenga en cuenta que las instrucciones individuales dentro de un bloque terminan en punto y coma, pero no el bloque en sí.  
  
 Por lo general, los bloques se utilizan en funciones y condicionales. Tenga en cuenta que, a diferencia de C++ y otros lenguajes, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] no considera que un bloque sea un ámbito nuevo; solo las funciones crean un ámbito.  
  
 En el ejemplo siguiente, la cláusula `else` contiene un bloque de dos instrucciones entre llaves. El bloque se trata como una sola instrucción. Además, la función en sí consiste en un bloque de instrucciones entre llaves. Las instrucciones situadas debajo de la función se encuentran fuera del bloque y, por lo tanto, no forman parte de la definición de la función.  
  
```JavaScript  
function inchestometers(inches)  
   {  
   if (inches < 0)  
      return -1;  
   else  
      {  
      var meters = inches / 39.37;  
      return meters;  
      }  
   }  
  
var inches = 12;  
var meters = inchestometers(inches);  
document.write("the value in meters is " + meters);  
```  
  
## <a name="comments"></a>Comentarios  
 Un comentario [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] de una sola línea comienza por un par de barras diagonales (//). A continuación se muestra un ejemplo de comentario de una sola línea.  
  
```JavaScript  
var aGoodIdea = "Comment your code thoroughly."; // This is a single-line comment.  
```  
  
 Un comentario [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] de varias líneas comienza por una barra diagonal y un asterisco (/\*) y termina con el orden inverso (\*/).  
  
```JavaScript  
/*  
This is a multiline comment that explains the preceding code statement.  
  
The statement assigns a value to the aGoodIdea variable. The value,   
which is contained between the quote marks, is called a literal. A   
literal explicitly and directly contains information; it does not   
refer to the information indirectly. The quote marks are not part   
of the literal.  
*/  
```  
  
> [!NOTE]
>  Si intenta insertar un comentario de varias líneas dentro de otro, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] interpreta el comentario de varias líneas resultante de forma inesperada. Los símbolos */ que marcan el final del comentario de varias líneas insertado se interpretan como el final de todo el comentario de varias líneas. Esto significa que el texto que sigue al comentario de varias líneas insertado no se marcará con comentarios, sino que se interpretará como código [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] y generará errores de sintaxis.  
  
 Se recomienda escribir todos los comentarios como bloques de comentarios de una línea. Esto le permite comentar más adelante segmentos de código extensos con un comentario de varias líneas.  
  
```JavaScript  
// This is another multiline comment, written as a series of single-line comments.  
// After the statement is executed, you can refer to the content of the   
// aGoodIdea variable by using its name.  
var extendedIdea = aGoodIdea + " You never know when you'll have to figure out what it does.";  
```  
  
## <a name="assignments-and-equality"></a>Asignaciones e igualdades  
 El signo igual (=) se utiliza en las instrucciones [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] para asignar valores a variables: es el operador de asignación. El operando izquierdo del operador = siempre es un valor Lvalue. Algunos ejemplos de valores Lvalue son:  
  
-   variables,  
  
-   elementos matriciales,  
  
-   propiedades de objeto.  
  
 El operando derecho del operador = siempre es un valor Rvalue. Los valores Rvalue pueden ser un valor arbitrario de cualquier tipo, incluido el valor de una expresión. A continuación se muestra un ejemplo de una instrucción de asignación [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```JavaScript  
var anInteger = 3;  
```  
  
 El compilador [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] interpreta esta instrucción como: "Asigna el valor 3 a la variable **anInteger**" o "**anInteger** toma el valor 3".  
  
 Asegúrese de comprender la diferencia entre el operador = (asignación) y el operador == (igualdad). Si quiere comparar dos valores para averiguar si son iguales, use dos signos igual (==). Esto se explica en detalle en [Controlar el flujo del programa](../javascript/controlling-program-flow-javascript.md).  
  
## <a name="expressions"></a>Expresiones  
 Un valor de expresión [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] puede ser de cualquier tipo [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] válido: un número, una cadena, un objeto, etcétera. Las expresiones más sencillas son literales. A continuación se muestran algunos ejemplos de expresiones literales [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```JavaScript  
3.9                       // numeric literal  
"Hello!"                  // string literal  
false                     // boolean literal  
null                      // literal null value  
{x:1, y:2}                // Object literal  
[1,2,3]                   // Array literal  
function(x){return x*x;}  // function literal  
```  
  
 Las expresiones más complejas pueden contener variables, llamadas de funciones y otras expresiones. Puede combinar expresiones para crear expresiones complejas con operadores. Algunos ejemplos de operadores son: `+` (suma), `-` (resta), `*` (multiplicación) y `/` (división).  
  
 A continuación se muestran algunos ejemplos de expresiones complejas [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```JavaScript  
var anExpression = 3 * (4 / 5) + 6;  
var aSecondExpression = Math.PI * radius * radius;  
var aThirdExpression = aSecondExpression + "%" + anExpression;  
var aFourthExpression = "(" + aSecondExpression + ") % (" + anExpression + ")";  
```