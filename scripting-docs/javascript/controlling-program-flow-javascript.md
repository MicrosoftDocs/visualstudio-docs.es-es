---
title: Controlar el flujo del programa (JavaScript) | Microsoft Docs
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
helpviewer_keywords:
- Boolean values, program flow
- continue statement
- break statement
- control flow, about control flow
ms.assetid: 4ef58c82-e5d6-4b09-9458-cf0aa3b39bf5
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20c256d26c6991067d7c25c0c835eda6e5e5aac6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="controlling-program-flow-javascript"></a>Controlar el flujo del programa (JavaScript)
Normalmente, las instrucciones de un script [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] se ejecutan una detrás de otra, en el orden en que se escriben. Esto se denomina ejecución secuencial y es la dirección predeterminada del flujo del programa.  
  
 Una alternativa a la ejecución secuencial transfiere el flujo de programa a otra parte del script. Es decir, en lugar de ejecutar la instrucción siguiente de la secuencia, se ejecuta otra instrucción.  
  
 Para que un script sea útil, esta transferencia del control se debe realizar de forma lógica. La transferencia del control de un programa se basa en una decisión cuyo resultado es una instrucción verdadera (que devuelve un valor booleano **true** o **false**). Cree una expresión y, a continuación, pruebe si su resultado es true. Hay dos clases principales de estructuras de programa que hacen esto.  
  
 La primera es la estructura de selección. Se usa para especificar rutas alternativas para el flujo del programa, creando de este modo un punto de unión en el programa (como un desvío en una carretera). En [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] hay disponibles cuatro estructuras de selección.  
  
-   la estructura de selección única (**if**),  
  
-   la estructura de selección doble (**if/else**),  
  
-   el operador ternario alineado `?:`  
  
-   la estructura de selección múltiple (`switch`).  
  
 El segundo tipo de estructura de control de programa es la estructura de repetición. Se usa para especificar que una acción se repetirá mientras alguna condición siga siendo verdadera. Cuando las condiciones de la instrucción de control se hayan cumplido (normalmente después de un número específico de repeticiones), el control se transferirá a la siguiente instrucción externa a la estructura de repetición. En [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] hay disponibles cuatro estructuras de repetición.  
  
-   la expresión se prueba en la parte superior del bucle (`while`)  
  
-   la expresión se prueba en la parte inferior del bucle (**do/while**),  
  
-   operar en cada propiedad de un objeto (**for/in**).  
  
-   repetición controlada mediante contador (**for**).  
  
 Puede crear scripts bastante complejos si anida y apila estructuras de control de selección y repetición.  
  
 El control de excepciones, que no se trata en este documento, proporciona una tercera forma de flujo de programa estructurado.  
  
## <a name="using-conditional-statements"></a>Uso de instrucciones condicionales  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] admite las instrucciones condicionales **if** e [if...else](../javascript/reference/if-dot-dot-dot-else-statement-javascript.md). En las instrucciones **if** se comprueba una condición; si esta supera la prueba, se ejecuta el código [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] pertinente. En la instrucción `if...else` se ejecuta código diferente si la condición no supera la prueba. La forma más sencilla de una instrucción **if** se puede escribir en una sola línea, pero es mucho más habitual usar instrucciones **if** y `if...else` de varias líneas.  
  
 En los ejemplos siguientes se muestran distintas sintaxis que se pueden utilizar con las instrucciones **if** y `if...else`. El primer ejemplo muestra el tipo de prueba booleana más sencilla. Si (y solo si) el elemento encerrado entre paréntesis da como resultado (o puede convertirse en) **true**, se ejecutará la instrucción o el bloque de instrucciones que siga a la instrucción **if**.  
  
```JavaScript  
function GetReaction(newShip, color, texture, dayOfWeek)  
{  
   // The test succeeds if the newShip Boolean value is true.  
   if (newShip)  
   {  
      return "Champagne Bottle";  
   }  
  
   // The test succeeds if both conditions are true.  
   if (color == "deep yellow" && texture == "large and small wrinkles")  
   {  
      return "Is it a crenshaw melon?";  
   }  
  
   // The test succeeds if either condition is true.  
   if ((dayOfWeek == "Saturday") || (dayOfWeek == "Sunday"))  
   {  
      return "I'm off to the beach!";  
   }  
   else  
   {  
      return "I'm going to work.";  
   }  
}  
  
var reaction = GetReaction(false, "deep yellow", "smooth", "Sunday");  
document.write(reaction);  
  
// Output: I'm off to the beach!  
```  
  
## <a name="conditional-operator"></a>Operador condicional  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] también admite una forma condicional implícita. Usa un signo de interrogación después de la condición que se va a probar (en lugar de la palabra **if** antes de la condición). También especifica dos alternativas: una se usará si se cumple la condición y otra si no se cumple. Estas alternativas deben estar separadas por un signo de dos puntos.  
  
```JavaScript  
var AMorPM = (theHour >= 12) ? "PM" : "AM";  
```  
  
 Si va a probar varias condiciones juntas y sabe que una tiene más posibilidades de cumplirse o de no cumplirse que las demás, puede usar una característica denominada 'evaluación de cortocircuito' para acelerar la velocidad de ejecución del script. Cuando [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] evalúa una expresión lógica, solo evalúa el número de subexpresiones necesario para obtener un resultado.  
  
 Por ejemplo, si tiene una expresión AND como ((x == 123) && (y == 6)), [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] compruebe primero si x es 123. Si no lo es, toda la expresión no puede ser true, aunque sea igual a 6. Por tanto, la prueba para y nunca se realiza y [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] devuelve el valor **false**.  
  
 Del mismo modo, si solo una de varias condiciones debe ser **true** (usando el operador &#124;&#124;), la prueba se detiene en cuanto una condición supera la prueba. Esto es válido si las condiciones que se van a comprobar implican la ejecución de llamadas a funciones u otras expresiones complejas. Con esta perspectiva, cuando escriba expresiones Or, ponga primero las condiciones que es más probable que sean **true**. Cuando escriba expresiones And, ponga primero las condiciones que es más probable que sean **false**.  
  
 Una ventaja de diseñar el script de esta manera es que **runsecond()** no se ejecutará en el ejemplo siguiente si **runfirst()** devuelve 0.  
  
```JavaScript  
if ((runfirst() == 0) || (runsecond() == 0)) {  
    // some code  
}  
```  
  
## <a name="using-loops"></a>Uso de bucles  
 Hay varias formas de ejecutar una instrucción o un bloque de instrucciones varias veces. En general, la ejecución repetitiva se denomina *ejecución en bucle* o *iteración*. Una iteración es simplemente una ejecución única de un bucle. Normalmente se controla mediante la prueba de una variable, en la que el valor cambia cada vez que se ejecuta el bucle. [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] admite cuatro tipos de bucles: [for](../javascript/reference/for-statement-javascript.md), [for...in](../javascript/reference/for-dot-dot-dot-in-statement-javascript.md), [while](../javascript/reference/while-statement-javascript.md) y [do...while](../javascript/reference/do-dot-dot-dot-while-statement-javascript.md).  
  
## <a name="using-for-loops"></a>Utilizar bucles for  
 La instrucción **for** especifica una variable de contador, una condición de prueba y una acción que actualiza el contador. La condición se comprueba antes de cada iteración del bucle. Si la comprobación es correcta, se ejecuta el código interior del bucle. En caso contrario, el código interior del bucle no se ejecuta y el programa continúa por la primera línea de código inmediatamente posterior al bucle. Después de ejecutar el bucle, la variable de contador se actualiza antes de comenzar la siguiente iteración.  
  
 Si nunca se cumple la condición del bucle, éste nunca se ejecuta. Si la condición del bucle se cumple siempre, el bucle se convierte en un proceso infinito. Aunque es posible que lo primero sea necesario en algunos casos, lo segundo raramente lo es, por lo que debe tener cuidado al escribir las condiciones de los bucles.  
  
```JavaScript  
// The update expression ("icount++" in the following examples)  
// is executed at the end of the loop, after the block of  
// statements that forms the body of the loop is executed, and  
// before the condition is tested.  
  
// Set a limit of 10 on the loop.  
var howFar = 10;  
  
// Create an array called sum with 10 members, 0 through 9.  
var sum = new Array(howFar);  
sum[0] = 0;  
  
// Iterate from 0 through 9.  
var theSum = 0;  
for(var icount = 0; icount < howFar; icount++)  
{  
   theSum += icount;  
   sum[icount] = theSum;  
}  
  
// This code is not executed at all, because icount is not greater than howFar.  
var newSum = 0;  
for(var icount = 0; icount > howFar; icount++)  
{  
   newSum += icount;  
}  
  
// This is an infinite loop.  
var sum = 0;  
for(var icount = 0; icount >= 0; icount++)  
{  
   sum += icount;  
}  
```  
  
## <a name="using-forin-loops"></a>Usar bucles for...in  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] proporciona una clase especial de bucle para recorrer todas las propiedades definidas por el usuario de un [objeto](../javascript/objects-and-arrays-javascript.md) o todos los elementos de una matriz. El contador de un bucle `for...in` es una cadena, no un número. Contiene el nombre de la propiedad actual o el índice del elemento de matriz actual.  
  
```JavaScript  
// Create an object with some properties  
var myObject = new Object();  
myObject.name = "James";  
myObject.age = "22";  
myObject.phone = "555 1234";  
  
// Enumerate (loop through)_all the properties in the object  
for (var prop in myObject)  
{  
    // This displays "The property 'name' is James", etc.  
    document.write("The property '" + prop + "' is " + myObject[prop]);  
    // New line.  
    document.write("<br />");    
}  
```  
  
 Aunque los bucles `for...in` parecen similares a los bucles `For Each...Next` de VBScript, no funcionan de la misma manera. El [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]**bucle for...in** itera las propiedades de objetos [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]. El bucle **For Each...Next** de VBScript itera los elementos de una colección. Para recorrer en bucle colecciones en [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], debe utilizar el objeto [Objeto enumerador](../javascript/reference/enumerator-object-javascript.md) o, si está presente, el método `forEach` del objeto de colección. Aunque algunos objetos, como los de Internet Explorer, admiten tanto el bucle **For Each...Next** de VBScript como el bucle [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]**for...in**, la mayoría de los objetos no los admiten.  
  
## <a name="using-while-loops"></a>Utilizar bucles while  
 Un bucle `while` es similar a un bucle **for**. La diferencia es que un bucle `while` no tiene una variable de contador o una expresión de actualización integrada. Si desea controlar la ejecución repetitiva de una instrucción o un bloque de instrucciones pero necesita una regla más compleja que simplemente "ejecutar este código n veces", use un bucle `while`. En el ejemplo siguiente se usa el modelo de objetos de Internet Explorer y un bucle `while` para plantear al usuario una pregunta sencilla.  
  
```JavaScript  
var x = 0;  
while ((x != 5) && (x != null))  
{  
    x = window.prompt("What is my favorite number?", x);  
}  
  
if (x == null)  
    window.alert("You gave up!");  
else  
    window.alert("Correct answer!");  
```  
  
> [!NOTE]
>  Puesto que los bucles `while` no tienen variables de contador explícitas integradas, tienen más posibilidades de crear bucles infinitos que otros tipos de bucles. Además, debido a que no es fácil detectar dónde y cuándo se actualiza la condición del bucle, hay muchas posibilidades de escribir accidentalmente un bucle `while` en el que la condición nunca se actualice. Por este motivo, debe tener precaución al diseñar bucles `while`.  
  
 Como se ha indicado anteriormente, también hay un bucle **do...while** en [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] similar al bucle while, salvo que se garantiza que se ejecuta siempre al menos una vez, ya que la condición se prueba al final del bucle, no al principio. Por ejemplo, el bucle anterior puede volverse a escribir de la siguiente manera:  
  
```JavaScript  
var x = 0;  
do  
{  
    x = window.prompt("What is my favorite number?", x);  
} while ((x != 5) && (x != null));  
  
if (x == null)  
    window.alert("You gave up!");  
else  
    window.alert("Correct answer!");  
```  
  
## <a name="using-break-and-continue-statements"></a>Utilizar instrucciones break y continue  
 En [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], la instrucción [break](../javascript/reference/break-statement-javascript.md) se usa para detener la ejecución de un bucle, si se cumple alguna condición. Tenga en cuenta que la instrucción **break** también se utiliza para salir de un bloque `switch`. La instrucción [continue](../javascript/reference/continue-statement-javascript.md) se puede usar para pasar inmediatamente a la siguiente iteración, pasando por alto el resto del bloque de código y actualizando al mismo tiempo la variable de contador si el bucle es **for** o `for...in`.  
  
 El ejemplo siguiente se basa en el ejemplo anterior; se usan las instrucciones**break** y **continue** para controlar el bucle.  
  
```JavaScript  
var x = 0;  
do  
{  
    x = window.prompt("What is my favorite number?", x);  
  
    // Did the user cancel? If so, break out of the loop  
    if (x == null)  
        break;  
  
    // Did they enter a number?  
    // If so, no need to ask them to enter a number.  
    if (Number(x) == x)  
        continue;  
  
    // Ask user to only enter in numbers  
    window.alert("Please only enter in numbers!");  
  
} while (x != 5)  
  
if (x != 5)  
    window.alert("You gave up!");  
else  
    window.alert("Correct answer!");  
```