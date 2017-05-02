---
title: "Variables (JavaScript) | Microsoft Docs"
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
  - "distinción de mayúsculas y minúsculas, nombre de variable de JavaScript"
  - "conversión"
ms.assetid: 12a450e5-4818-4a09-9878-cd7c6cd2a248
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Variables (JavaScript)
En [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], una variable contiene un valor, por ejemplo "hola" o 5.  Cuando se utiliza la variable, se hace referencia a los datos que representa, por ejemplo, `NumberOfDaysLeft = EndDate – TodaysDate`.  
  
 Las variables se usan para almacenar, recuperar y manipular los valores que aparecen en el código.  Intenta asignar a las variables nombres descriptivos. Así, a los demás les resultará más fácil entender qué hace el código.  
  
## Declarar variables  
 La primera vez que aparece una variable en un script, es su declaración.  La primera mención de la variable la configura en la memoria, para que puedas hacer referencia a ella más adelante en el script.  Hay que declarar las variables antes de utilizarlas.  Para ello, se usa la palabra clave `var`.  
  
```javascript  
// A single declaration.  
var count;    
// Multiple declarations with a single var keyword.  
var count, amount, level;      
// Variable declaration and initialization in one statement.  
var count = 0, amount = 100;   
```  
  
 Si no inicializas la variable en la instrucción `var`, toma automáticamente el valor `undefined`.  
  
## Nombres de variables  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] es un lenguaje que distingue mayúsculas de minúsculas.  Esto significa que un nombre de variable como miContador es distinto del nombre de variable MIContador.  Los nombres de variable pueden tener cualquier longitud.  Las reglas para crear nombres de variable válidos son las siguientes:  
  
-   El primer carácter debe ser una letra ASCII \(en mayúsculas o minúsculas\) o un carácter de subrayado \(\_\).  No puede utilizarse un número como primer carácter.  
  
-   Los siguientes caracteres deben ser letras, números o caracteres de subrayado \(\_\).  
  
-   El nombre de una variable no puede ser una [palabra reservada](../javascript/reference/javascript-reserved-words.md).  
  
 A continuación se muestran algunos ejemplos de nombres de variables válidos:  
  
```  
_pagecount   
Part9   
Number_Items   
```  
  
 A continuación se muestran algunos ejemplos de nombres de variables no válidos:  
  
```javascript  
// Cannot begin with a number.   
99Balloons     
// The ampersand (&) character is not a valid character for variable names.   
Alpha&Beta   
```  
  
 Cuando quieras declarar una variable e inicializarla, pero no quieras darle ningún valor determinado, asígnale el valor `null`.  A continuación se muestra un ejemplo.  
  
```javascript  
var bestAge = null;  
var muchTooOld = 3 * bestAge; // muchTooOld has the value 0.  
```  
  
 Si declaras una variable sin asignarle un valor, tendrá el valor `undefined`.  A continuación se muestra un ejemplo.  
  
```javascript  
var currentCount;  
// finalCount has the value NaN because currentCount is undefined.  
var finalCount = 1 * currentCount;   
```  
  
 El valor `null` se comporta como el número 0, mientras que `undefined` se comporta como el valor especial `NaN` \(no es un número\).  Si comparas un valor `null` con un valor `undefined`, son iguales.  
  
 Puedes declarar una variable sin utilizar la palabra clave `var` en la declaración y asignarle un valor.  Se trata de una declaración implícita.  
  
```javascript  
// The variable noStringAtAll is declared implicitly.  
noStringAtAll = "";   
```  
  
 No se puede utilizar una variable que nunca se haya declarado.  
  
```javascript  
// Error. Length and width do not yet exist.  
var area = length * width;   
```  
  
## Conversión  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] es un lenguaje con establecimiento flexible de tipos, en comparación con los lenguajes fuertemente tipados como C\+\+.  Esto significa que las variables de JavaScript no tienen ningún tipo predeterminado.  En cambio, el tipo de una variable es el tipo de su valor.  Este comportamiento permite tratar un valor como si fuera de un tipo diferente.  
  
 En [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], puedes realizar operaciones con valores de tipos diferentes sin provocar una excepción.  El intérprete de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] *convierte* implícitamente uno de los tipos de datos en el otro tipo y, después, realiza la operación.  Las reglas de conversión de los valores alfanuméricos, numéricos y booleanos son las siguientes:  
  
-   Si se suman un número y una cadena, el número se convierte en una cadena.  
  
-   Si se suman un valor booleano y una cadena, el tipo booleano se convierte en una cadena.  
  
-   Si se suman un número y un valor booleano, el tipo booleano se convierte en un número.  
  
 En el ejemplo siguiente, un número sumado a una cadena produce una cadena.  
  
```javascript  
var x = 2000;  
var y = "Hello";  
// The number is coerced to a string.  
x = x + y;  
document.write(x);   
  
// Output:  
// 2000Hello  
```  
  
 Las cadenas se convierten automáticamente en números equivalentes para compararlos.  Para convertir de forma explícita una cadena en un entero, usa la [función parseInt](../javascript/reference/parseint-function-javascript.md).  Para convertir de forma explícita una cadena en un número, usa la [función parseFloat](../javascript/reference/parsefloat-function-javascript.md).