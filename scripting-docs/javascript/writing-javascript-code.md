---
title: "Escribir c&#243;digo JavaScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.htmldesigner.html"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "código, JavaScript (sintaxis)"
  - "comentarios, código de JavaScript"
  - "código de JavaScript"
ms.assetid: dde28266-0d0f-4460-a819-f931cf0911ad
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Escribir c&#243;digo JavaScript
Como muchos otros lenguajes de programación, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] está organizado en instrucciones, bloques que constan de conjuntos relacionados de instrucciones y comentarios.  Dentro de una instrucción puedes usar variables, cadenas, números y expresiones.  
  
## Instrucciones  
 Un programa de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] es una colección de instrucciones.  Las instrucciones de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] agrupan expresiones de tal forma que realizan una tarea completa.  
  
 Una instrucción se compone de una o varias expresiones, palabras claves u operadores \(símbolos\).  Normalmente, una instrucción se escribe en una sola línea, aunque una instrucción se puede escribir en dos o más líneas.  Además, se pueden escribir dos o más instrucciones en la misma línea si se separan mediante signos de punto y coma.  En general, cada línea nueva inicia una nueva instrucción.  Es conveniente finalizar las instrucciones explícitamente.  Para ello se usa el punto y coma \(;\), que es el carácter de terminación de instrucciones de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
 A continuación se incluyen dos ejemplos de instrucciones de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  Las frases que hay después de los caracteres \/\/ son *comentarios*, que son notas explicativas en el programa.  
  
```javascript  
var aBird = "Robin"; // Assign the text "Robin" to the variable aBird.  
var today = new Date(); // Assign today's date to the variable today.  
```  
  
 Un grupo de instrucciones de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] rodeadas de llaves \({}\) se denomina un *bloque*.  Por lo general, las instrucciones agrupadas en un bloque pueden tratarse como una sola instrucción.  Esto significa que puedes usar bloques en la mayoría de los lugares en los que [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] espera encontrar una sola instrucción.  Las excepciones más notables a esta regla son los encabezados de los bucles **for** y `while`.  Ten en cuenta que las instrucciones únicas de un bloque finalizan con signos de punto y coma, pero no así el propio bloque.  
  
 En general, los bloques se usan en funciones y condiciones.  Observa que a diferencia de lo que ocurre en C\+\+ y otros lenguajes, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] no considera un bloque como un ámbito nuevo; solo las funciones crean un nuevo ámbito.  
  
 En el ejemplo siguiente, la cláusula `else` contiene un bloque de dos instrucciones entre llaves.  El bloque se trata como una única instrucción.  Además, la propia función consta de un bloque de instrucciones entre llaves.  Las instrucciones que hay debajo de la función están fuera del bloque y, por tanto, no forman parte de la definición de función.  
  
```javascript  
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
  
## Comentarios  
 Un comentario de una sola línea en [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] comienza con un par de barras diagonales \(\/\/\).  A continuación se muestra un ejemplo de comentario de una sola línea.  
  
```javascript  
var aGoodIdea = "Comment your code thoroughly."; // This is a single-line comment.  
```  
  
 Un comentario de varias líneas de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] comienza con una barra diagonal seguida de un asterisco \(\/\*\) y termina con los mismos elementos en orden inverso \(\*\/\).  
  
```javascript  
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
>  Si intentas incrustar un comentario de varias líneas dentro de otro, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] interpreta el comentario de varias líneas resultante de forma inesperada.  Los caracteres \*\/ que marcan el final del comentario de varias líneas incrustado se interpretan como el final de todo el comentario de varias líneas.  Esto significa que el texto que sigue al comentario incrustado de varias líneas no se marcará como comentario; en su lugar, se interpretará como código de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] y generará errores de sintaxis.  
  
 Se recomienda que escribas todos tus comentarios como bloques de comentarios de una sola línea.  Esto te permitirá poner como comentarios extensos segmentos de código mediante un comentario de varias líneas posteriormente.  
  
```javascript  
// This is another multiline comment, written as a series of single-line comments.  
// After the statement is executed, you can refer to the content of the   
// aGoodIdea variable by using its name.  
var extendedIdea = aGoodIdea + " You never know when you'll have to figure out what it does.";  
```  
  
## Asignaciones e igualdad  
 El signo igual \(\=\) se usa en las instrucciones de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] para asignar valores a variables: es el operador de asignación.  El operando situado a la izquierda del operador \= siempre es un valor L.  He aquí algunos ejemplos de valores L:  
  
-   variables,  
  
-   elementos de matriz,  
  
-   propiedades de objeto.  
  
 El operando situado a la derecha del operador \= siempre es un valor R.  Los valores R puedes ser cualquier tipo de valor arbitrario, incluido el valor de una expresión.  A continuación se incluye un ejemplo de instrucción de asignación de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```javascript  
var anInteger = 3;  
```  
  
 El compilador de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] interpreta esta instrucción de la forma siguiente: "Asignar el valor 3 a la variable **anInteger**" o "**anInteger** toma el valor 3".  
  
 Es importante comprender la diferencia que hay entre los operadores \= \(asignación\) y \=\= \(igualdad\).  Si deseas comparar dos valores para averiguar si son iguales, usa dos signos igual \(\=\=\).  Esto se explica en detalle en [Controlar el flujo del programa](../javascript/controlling-program-flow-javascript.md).  
  
## Expresiones  
 Un valor de expresión de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] puede ser de cualquier tipo válido de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]: un número, una cadena, un objeto, etc.  Las expresiones más sencillas son literales.  A continuación se incluyen algunos ejemplos de expresiones con literales de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]:  
  
```javascript  
3.9                       // numeric literal  
"Hello!"                  // string literal  
false                     // boolean literal  
null                      // literal null value  
{x:1, y:2}                // Object literal  
[1,2,3]                   // Array literal  
function(x){return x*x;}  // function literal  
```  
  
 Las expresiones más complejas pueden incluir variables, llamadas a funciones y otras expresiones.  Puedes agrupar expresiones para crear expresiones complejas mediante operadores.  Ejemplos de operadores son: `+` \(suma\), `-` \(resta\), `*` \(multiplicación\) y `/` \(división\).  
  
 A continuación se incluyen algunos ejemplos de expresiones complejas de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```javascript  
var anExpression = 3 * (4 / 5) + 6;  
var aSecondExpression = Math.PI * radius * radius;  
var aThirdExpression = aSecondExpression + "%" + anExpression;  
var aFourthExpression = "(" + aSecondExpression + ") % (" + anExpression + ")";  
```