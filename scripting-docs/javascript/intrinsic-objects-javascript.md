---
title: Objetos intrínsecos (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- built-in objects [JavaScript]
- intrinsic objects [JavaScript]
ms.assetid: 6520c634-a7d1-4a05-8c1b-2e79f449d2e4
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 242b572c2818f9968e6d5fc51e1272e3004c0f05
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569615"
---
# <a name="intrinsic-objects-javascript"></a>Objetos intrínsecos (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] proporciona los objetos intrínsecos (o "integrados"). Se trata de los objetos `Array`, `Boolean`, `Date`, `Error`, `Function`, **Global**, **JSON**, **Math**, **Number**, `Object`, `RegExp`, y `String`. Los objetos intrínsecos tienen asociados métodos, funciones, propiedades y constantes que se describen en detalle en la [referencia de lenguaje](../javascript/reference/javascript-reference.md).  
  
## <a name="array-object"></a>Array (Objeto)  
 Los subíndices de una matriz pueden considerarse propiedades de un objeto y se hace referencia a ellos mediante su índice numérico. Tenga en cuenta que las propiedades con nombre agregadas a una matriz no pueden indizarse por número; son independientes de los elementos de matriz.  
  
 Para crear una matriz, use el operador **new** y el [constructor](../javascript/reference/constructor-property-object-javascript.md) **Array()**, como en el ejemplo siguiente.  
  
```JavaScript  
var theMonths = new Array(12);  
theMonths[0] = "Jan";  
theMonths[1] = "Feb";  
theMonths[2] = "Mar";  
theMonths[3] = "Apr";  
theMonths[4] = "May";  
theMonths[5] = "Jun";  
theMonths[6] = "Jul";  
theMonths[7] = "Aug";  
theMonths[8] = "Sep";  
theMonths[9] = "Oct";  
theMonths[10] = "Nov";  
theMonths[11] = "Dec";  
```  
  
 Cuando se crea una matriz mediante la palabra clave `Array`, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] incluye una propiedad **length**, que registra el número de entradas. Si no especifica un número, la longitud se establece en 0 y la matriz no tiene ninguna entrada. Si especifica un número, la longitud se establece en ese número. Si especifica más de un parámetro, los parámetros se usan como entradas de la matriz. Además, el número de parámetros se asigna a la propiedad length, como se muestra en el ejemplo siguiente, que es equivalente al ejemplo anterior.  
  
```JavaScript  
var theMonths = new Array("Jan", "Feb", "Mar", "Apr", "May", "Jun",   
"Jul", "Aug", "Sep", "Oct", "Nov", "Dec");  
```  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] cambia automáticamente el valor de **length** cuando agrega elementos a una matriz creada con la palabra clave `Array`. Los índices de matriz de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] siempre empiezan con 0, no con 1, por lo que la propiedad length es siempre una unidad mayor que el índice más grande de la matriz.  
  
## <a name="string-object"></a>String (Objeto)  
 En [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], puede tratar las cadenas (y los números) como si fueran objetos. El [objeto string](../javascript/reference/string-object-javascript.md) tiene varios métodos integrados que puede usar con las cadenas. Uno de ellos es el [método substring](../javascript/reference/substring-method-string-javascript.md), que devuelve parte de la cadena. Usa dos números como argumentos.  
  
```JavaScript  
var aString = "0123456789";  
  
// This code sets aChunk to "456".  
var aChunk = aString.substring(4, 7);  
  
// This code sets anotherChunk to "456", using  
// the lower value index as the starting index.  
var anotherChunk = aString.substring(7, 4);  
  
// This code sets the firstLetter variable to "J"  
// by using the array in the preceding array creation example.  
firstLetter = theMonths[5].substring(0,1);  
```  
  
 Otra propiedad del objeto `String` es **length**. Esta propiedad contiene el número de caracteres de la cadena (0 para una cadena vacía). Se trata de un valor numérico que puede usar directamente en los cálculos.  
  
```JavaScript  
var howLong = "Hello World".length  // Sets the howLong variable to 11.  
```  
  
## <a name="math-object"></a>Math (Objeto)  
 El objeto **Math** tiene un número de constantes y funciones predefinidas. Las constantes son números específicos. Uno de estos números específicos es el valor de pi (aproximadamente 3,14159...). Esta es la constante **Math.PI**, que se muestra en el ejemplo siguiente.  
  
```JavaScript  
var radius = 5;  
var circleArea = Math.PI * radius * radius;  
```  
  
 Una de las funciones integradas del objeto **Math** es el método de exponenciación, o `Math.pow`, que eleva un número a una potencia especificada. En el ejemplo siguiente se usa pi y exponenciación para calcular el volumen de una esfera.  
  
```JavaScript  
var volume = (4/3)*(Math.PI*Math.pow(radius,3));  
```  
  
## <a name="date-object"></a>Date (Objeto)  
 El objeto `Date` puede usarse para representar fechas y horas arbitrarias, para obtener la fecha actual del sistema y para calcular diferencias entre fechas. Tiene varias propiedades y métodos, todos ellos predefinidos. En general, el objeto `Date` proporciona el día de la semana; el mes, el día y el año; y la hora en horas, minutos y segundos. Esta información se basa en el número de milisegundos desde el 1 de enero de 1970, 00:00:00.000 GMT, que es la hora del meridiano de Greenwich (el término preferido es UTC u "hora universal coordinada", que hace referencia a las señales emitidas por el estándar de hora mundial). [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] puede administrar fechas que se encuentran en el intervalo aproximado de 250.000 a. C. a 255.000 d. C.  
  
 Para crear un nuevo objeto `Date`, use el operador **new**, como se muestra en el ejemplo siguiente.  
  
```JavaScript  
var toDay = new Date();    
var thisYear = toDay.getFullYear();  
var thisMonth = theMonths[toDay.getMonth()];  
var thisDay = thisMonth  + " " + toDay.getDate() + ", " + thisYear;  
```  
  
## <a name="number-object"></a>Number (Objeto)  
 Además de las constantes numéricas especiales (por ejemplo, `PI`) que están disponibles en el objeto **Math**, hay otras constantes disponibles en [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] a través del objeto **Number**.  
  
|Constante|Descripción|  
|--------------|-----------------|  
|Number.MAX_VALUE|Mayor número posible, aproximadamente 1,79E+308; puede ser positivo o negativo. (Su valor varía ligeramente según el sistema).|  
|Number.MIN_VALUE|Menor número posible, aproximadamente 5,00E-324; puede ser positivo o negativo. (Su valor varía ligeramente según el sistema).|  
|Number.NaN|Valor no numérico especial ("not a number").|  
|Number.POSITIVE_INFINITY|Cualquier valor positivo mayor que el mayor número positivo (Number.MAX_VALUE) se convierte automáticamente a este valor; se representa como infinito.|  
|Number.NEGATIVE_INFINITY|Cualquier valor negativo mayor que el mayor número negativo (-Number.MAX_VALUE) se convierte automáticamente a este valor; se representa como -infinito.|  
  
 **Number.NaN** es una constante especial que se define como "no es un número". Un intento de analizar una cadena que no se puede analizar como número devuelve **Number.NaN**. `NaN` se compara como diferente a cualquier número y a sí mismo. Para probar un resultado `NaN`, no compare con **Number.NaN**; use la función **isNaN()**.  
  
## <a name="json-object"></a>JSON (Objeto)  
 JSON es un formato de intercambio de datos ligero basado en un subconjunto de la notación literal de objetos del lenguaje JavaScript.  
  
 El objeto JSON proporciona dos funciones para convertir al formato de texto JSON y desde este. La función [JSON.stringify](../javascript/reference/json-stringify-function-javascript.md) serializa objetos y matrices en texto JSON. La función [JSON.parse](../javascript/reference/json-parse-function-javascript.md) deserializa texto JSON para generar objetos en memoria. Para obtener más información, consulte [Introducción a JavaScript Object Notation (JSON) en JavaScript y .NET](http://go.microsoft.com/fwlink/?LinkId=124098).  
  
## <a name="see-also"></a>Vea también  
 [Objetos de JavaScript](../javascript/reference/javascript-objects.md)