---
title: Variables (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- coercion
- case sensitivity, JavaScript variable name
ms.assetid: 12a450e5-4818-4a09-9878-cd7c6cd2a248
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: f30946899ad35286dfb1e786cf903d58f5c98cb6
ms.contentlocale: es-es
ms.lasthandoff: 08/11/2017

---
# <a name="variables-javascript"></a>Variables (JavaScript)
En [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], una variable contiene un valor, por ejemplo, "hola" o 5. Cuando se usa la variable, se hace referencia a los datos que esta representa, por ejemplo `NumberOfDaysLeft = EndDate - TodaysDate`.  
  
 Las variables se usan para almacenar, recuperar y manipular valores que aparecen en el código. Intente asignar a las variables nombres descriptivos para ayudar a otras personas a comprender fácilmente lo que hace su código.  
  
## <a name="declaring-variables"></a>Declaración de variables  
 La primera vez que una variable aparece en su script es su declaración. La primera mención de la variable la pone en memoria, por lo que puede hacer referencia a ella más adelante en el script. Antes de poder usar las variables debe declararlas. Para ello, se usa la palabra clave `var`.  
  
```JavaScript  
// A single declaration.  
var count;    
// Multiple declarations with a single var keyword.  
var count, amount, level;      
// Variable declaration and initialization in one statement.  
var count = 0, amount = 100;   
```  
  
 Si no inicializa la variable en la instrucción `var`, toma automáticamente el valor `undefined`.  
  
## <a name="naming-variables"></a>Nomenclatura de variables  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] es un lenguaje que distingue mayúsculas de minúsculas. Esto significa que un nombre de variable como **miContador** es diferente del nombre de variable **MIContador**. Los nombres de variable pueden tener cualquier longitud. Las reglas para crear nombres de variable válidos son las siguientes:  
  
-   El primer carácter debe ser una letra ASCII (en mayúsculas o minúscula) o un carácter de subrayado (_). Tenga en cuenta que no se puede usar un número como primer carácter.  
  
-   Los caracteres siguientes deben ser letras, números o caracteres de subrayado (_).  
  
-   El nombre de variable no debe ser una [palabra reservada](../javascript/reference/javascript-reserved-words.md).  
  
 Estos son algunos ejemplos de nombres de variable válidos:  
  
```  
_pagecount   
Part9   
Number_Items   
```  
  
 Estos son algunos ejemplos de nombres de variable no válidos:  
  
```JavaScript  
// Cannot begin with a number.   
99Balloons     
// The ampersand (&) character is not a valid character for variable names.   
Alpha&Beta   
```  
  
 Cuando quiere declarar una variable e inicializarla, pero no desea proporcionarle ningún valor en particular, asígnele el valor `null`. A continuación se muestra un ejemplo.  
  
```JavaScript  
var bestAge = null;  
var muchTooOld = 3 * bestAge; // muchTooOld has the value 0.  
```  
  
 Si se declara una variable sin asignarle un valor, tendrá el valor `undefined`. A continuación se muestra un ejemplo.  
  
```JavaScript  
var currentCount;  
// finalCount has the value NaN because currentCount is undefined.  
var finalCount = 1 * currentCount;   
```  
  
 El valor `null` se comporta como el número 0, mientras que `undefined` se comporta como el valor especial `NaN` (Not a Number). Si se compara un valor `null` y un valor `undefined`, son iguales.  
  
 Puede declarar una variable sin usar la palabra clave `var` en la declaración y asignarle un valor. Esta es una declaración implícita.  
  
```JavaScript  
// The variable noStringAtAll is declared implicitly.  
noStringAtAll = "";   
```  
  
 No se puede usar una variable que nunca se ha declarado.  
  
```JavaScript  
// Error. Length and width do not yet exist.  
var area = length * width;   
```  
  
## <a name="coercion"></a>Conversión  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] es un lenguaje débilmente tipado, por oposición a lenguajes fuertemente tipados como C++. Esto significa que las variables de JavaScript no tienen ningún tipo predeterminado. En su lugar, el tipo de una variable es el tipo de su valor. Este comportamiento permite tratar un valor como si fuera de un tipo diferente.  
  
 En [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], puede realizar operaciones en valores de tipos diferentes sin producir una excepción. El intérprete [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] transforma, o *convierte* implícitamente, uno de los tipos de datos en el tipo del otro, y luego realiza la operación. Las reglas de conversión de valores de cadena, número y booleanos son las siguientes:  
  
-   Si agrega un número y una cadena, el número se convierte en una cadena.  
  
-   Si agrega un valor booleano y una cadena, el valor booleano se convierte en una cadena.  
  
-   Si agrega un número y un valor booleano, el valor booleano se convierte en un número.  
  
 En el ejemplo siguiente, un número agregado a una cadena tiene como resultado una cadena.  
  
```JavaScript  
var x = 2000;  
var y = "Hello";  
// The number is coerced to a string.  
x = x + y;  
document.write(x);   
  
// Output:  
// 2000Hello  
```  
  
 Las cadenas se convierten automáticamente en números equivalentes con fines de comparación. Para convertir explícitamente una cadena en un entero, use la función [parseInt](../javascript/reference/parseint-function-javascript.md). Para convertir explícitamente una cadena en un número, use la función [parseFloat](../javascript/reference/parsefloat-function-javascript.md).
