---
title: Tipos de datos (JavaScript) | Microsoft Docs
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
helpviewer_keywords: Boolean data type, supported data types
ms.assetid: c7a6bd3a-4b1c-4dbe-8505-106dbf483b41
caps.latest.revision: "35"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aa3a0e4cdbb25019758f89958afdf06c11f01a34
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="data-types-javascript"></a>Tipos de datos (JavaScript)
En [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], hay tres tipos de datos principales, dos tipos de datos compuestos y dos tipos de datos especiales.  
  
## <a name="primary-data-types"></a>Tipos de datos principales  
 Tipos de datos principales (primitivos):  
  
-   String  
  
-   Número  
  
-   Booleano  
  
## <a name="composite-data-types"></a>Tipos de datos compuestos  
 Tipos de datos compuestos (referencia):  
  
-   Objeto  
  
-   Matriz  
  
## <a name="special-data-types"></a>Tipos de datos especiales  
 Tipos de datos especiales:  
  
-   Null  
  
-   Sin definir  
  
## <a name="string-data-type"></a>String (Tipo de datos)  
 Un valor de cadena es una cadena de cero o más caracteres Unicode (letras, dígitos y signos de puntuación). Utilice el tipo de datos de cadena para representar texto en [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]. Encierre los literales de cadena entre comillas simples o dobles para incluirlos en los scripts. Las comillas dobles pueden incluirse en cadenas delimitadas por comillas simples, y las comillas simples pueden incluirse en cadenas delimitadas por comillas dobles. A continuación se incluyen ejemplos de cadenas:  
  
```JavaScript  
"Happy am I; from care I'm free!"  
'"Avast, ye lubbers!" roared the technician.'   
"45"  
'c'  
```  
  
 Tenga en cuenta que [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] no tiene ningún tipo para representar un único carácter. Para representar un único carácter en [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], cree una cadena que conste de un solo carácter. Una cadena que no contiene caracteres ("") es una cadena vacía (longitud cero).  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] proporciona secuencias de escape que se pueden incluir en cadenas para crear caracteres que no es posible escribir directamente. Por ejemplo, `\t` especifica un carácter de tabulación. Para obtener más información, consulte [Caracteres especiales](../javascript/advanced/special-characters-javascript.md).  
  
## <a name="number-data-type"></a>Tipo de datos numéricos  
 En [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], no se distingue entre valores enteros y valores de punto flotante; un número [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] puede ser cualquiera (internamente, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] representa todos los números como valores de punto flotante).  
  
### <a name="integer-values"></a>Valores enteros  
 Los valores enteros pueden ser números enteros positivos, enteros negativos y 0. Se pueden representar en base 10 (decimal), base 16 (hexadecimal) y base 8 (octal). Casi todos los números en [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] se escriben en formato decimal.  
  
 Para indicar enteros hexadecimales ("hex"), agrégueles el prefijo "0x" (cero y x&#124;X). Solo pueden contener dígitos del 0 al 9 y letras de la A a la F (en mayúscula o minúscula). Las letras de la A a la F se utilizan para representar, como dígitos únicos, del 10 al 15 en base 10. Es decir, 0xF equivale a 15 y 0x10 equivale a 16.  
  
 Para indicar enteros octales, agrégueles el prefijo "0" (cero). Solo pueden contener dígitos del 0 al 7. Un número que tiene un "0" inicial y contiene los dígitos "8" o "9" se interpreta como un número decimal.  
  
 Los números octales y hexadecimales pueden ser negativos, pero no pueden tener una parte decimal ni pueden escribirse en notación científica (exponencial).  
  
> [!NOTE]
>  A partir de [!INCLUDE[jsv9text](../javascript/includes/jsv9text-md.md)], la [función parseInt](../javascript/reference/parseint-function-javascript.md) no trata una cadena que contenga un prefijo "0" como octal. Sin embargo, cuando no se utiliza la función `parseInt`, las cadenas con el prefijo "0" aún se pueden interpretar como octales.  
  
### <a name="floating-point-values"></a>Valores de punto flotante  
 Los valores de punto flotante pueden ser números enteros con una parte decimal. Además, pueden expresarse en notación científica. Es decir, una letra mayúscula o minúscula "e" se utiliza para representar "diez a la potencia de". [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] representa números mediante el estándar de punto flotante IEEE 754 de ocho bytes para la representación numérica. Esto significa que puede escribir números tan grandes como 1.79769x10<sup>308</sup> y tan pequeños como 5x10<sup>-324</sup>. Un número que contiene un separador decimal y solo tiene un "0" antes se interpreta como un número de punto flotante decimal.  
  
 Tenga en cuenta que un número que comience por "0x" o "00" y contenga un separador decimal generará un error. A continuación se incluyen algunos ejemplos de números [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
|Número|Descripción|Valor decimal equivalente|  
|------------|-----------------|------------------------|  
|.0001, 0.0001, 1e-4, 1.0e-4|Cuatro números de punto flotante equivalentes.|0.0001|  
|3.45e2|Número en punto flotante.|345|  
|45|Entero.|45|  
|0378|Entero. Aunque parezca un número octal (comienza con un cero), 8 no es un dígito octal válido, por lo que el número se trata como un valor decimal.|378|  
|0377|Entero octal. Tenga en cuenta que aunque parezca que solo sea uno menos que el número anterior, su valor real es bastante diferente.|255|  
|0.0001|Número de punto flotante. Aunque comience con un cero, no es un número octal porque tiene un separador decimal.|0.0001|  
|00.0001|Se trata de un error. Los dos primeros ceros marcan el número como un octal, pero los octales no pueden tener un componente decimal.|No procede (error del compilador)|  
|0Xff|Entero hexadecimal.|255|  
|0x37CF|Entero hexadecimal.|14287|  
|0x3e7|Entero hexadecimal. Tenga en cuenta que 'e' no se trata como exponenciación.|999|  
|0x3.45e2|Se trata de un error. Los números hexadecimales no pueden tener partes decimales.|No procede (error del compilador)|  
  
 Además, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] contiene números con valores especiales. Estos son:  
  
-   NaN (no es un número). Se utiliza cuando se realiza una operación matemática en datos inapropiados, como cadenas o el valor no definido  
  
-   Infinito positivo. Se utiliza cuando un número positivo es demasiado grande para representarlo en [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
-   Infinito negativo. Se utiliza cuando un número negativo es demasiado grande para representarlo en [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
-   0 positivo y negativo. [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] diferencia entre cero positivo y negativo.  
  
## <a name="boolean-data-type"></a>Tipo de datos booleano  
 Mientras que la cadena y los tipos de datos numéricos pueden tener un número prácticamente ilimitado de valores diferentes, el tipo de datos booleano solo puede tener dos. Son los literales `true` y `false`. Un valor booleano es un valor de verdad: especifica si la condición es true o no.  
  
 Las comparaciones realizadas en los scripts siempre tienen un resultado booleano. Considere la siguiente línea de código [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```JavaScript  
y = (x == 2000);  
```  
  
 Aquí, el valor de la variable `x` se compara con el número 2000. Si es así, el resultado de la comparación es el valor booleano **true**, que se asigna a la variable `y`. Si `x` no es igual a 2000, entonces el resultado de la comparación es el valor booleano `false`.  
  
 Los valores booleanos son especialmente útiles en las estructuras de control. El código siguiente combina una comparación que crea un valor booleano directamente con una instrucción que lo utiliza. Considere el código de ejemplo [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] siguiente.  
  
```JavaScript  
if (x == 2000) {  
    z = z + 1;  
}  
else {  
    x = x + 1;  
}  
```  
  
 La instrucción `if/else` en [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] lleva a cabo una acción si un valor booleano es `true` (`z = z + 1`) y una acción alternativa si el valor booleano es `false` (`x = x + 1`).  
  
 Puede utilizar cualquier expresión como expresión comparativa. Cualquier expresión que se evalúa como 0, null, indefinida o una cadena vacía se interpreta como `false`. Una expresión que se evalúa como cualquier otro valor se interpreta como `true`. Por ejemplo, podría utilizar una expresión como:  
  
```JavaScript  
// This may not do what you expect. See below!  
if (x = y + z)   
```  
  
 Tenga en cuenta que la línea anterior no verifica si `x` es igual a `y + z`, ya que se utiliza únicamente un solo signo igual (el operador de asignación). En su lugar, el código anterior asigna el valor de `y + z` a la variable `x` y, a continuación, verifica si el resultado de la expresión completa (el valor de `x`) es cero. Para verificar si `x` es igual a `y + z`, debe usar el código siguiente.  
  
```JavaScript  
// This is different from the code above!  
if (x == y + z)   
```  
  
 Para obtener más información sobre las comparaciones, consulte [Controlar el flujo del programa](../javascript/controlling-program-flow-javascript.md).  
  
## <a name="the-null-data-type"></a>El tipo de datos NULL  
 El tipo de datos `null` solo tiene un valor en [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]: null. No se puede utilizar la palabra clave `null` como el nombre de una función o variable.  
  
 Una variable que contenga `null` no contiene ningún número, cadena, booleano, matriz u objeto válido. Puede borrar el contenido de una variable (sin eliminarla) asignándole el valor `null`.  
  
 Observe que en [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], `null` no es igual a 0 (como en C y C++). Tenga en cuenta también que el operador `typeof` en [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] notifica que los valores `null` son de tipo `Object`, no de tipo `null`. Este comportamiento potencialmente confuso es para la compatibilidad con versiones anteriores.  
  
## <a name="the-undefined-data-type"></a>El tipo de datos undefined  
 El valor `undefined` se devuelve al usar una propiedad de objeto que no existe, o una variable que se ha declarado, pero que nunca ha tenido un valor asignado.  
  
 para verificar si existe una variable, puede compararla con `undefined`, aunque puede saber si su tipo es `undefined` comparando el tipo de la variable con la cadena "undefined". En el ejemplo siguiente se muestra cómo averiguar si la variable `x` se ha declarado:  
  
```JavaScript  
  
var x;  
  
// This method works.  
if (x == undefined) {  
    document.write("comparing x to undefined <br/>");  
}  
.  
// This method doesn't work - you must check for the string "undefined".  
if (typeof(x) == undefined) {  
    document.write("comparing the type of x to undefined <br/>");  
}  
// This method does work.   
if (typeof(x) == "undefined") {  
    document.write("comparing the type of x to the string 'undefined'");  
}  
  
// Output:   
// comparing x to undefined   
// comparing the type of x to the string 'undefined'  
  
```  
  
 También puede comparar el valor indefinido con `null`. Esta comparación es `true` si la propiedad `someObject.prop` es `null` o si la propiedad `someObject.prop` no existe.  
  
```JavaScript  
someObject.prop == null;  
```  
  
 Para averiguar si existe una propiedad de objeto, puede usar el operador **in**:  
  
```JavaScript  
if ("prop" in someObject)  
    // someObject has the property 'prop'  
```  
  
## <a name="see-also"></a>Vea también  
 [Objetos y matrices](../javascript/objects-and-arrays-javascript.md)   
 [typeOf (operador)](../javascript/reference/typeof-operator-decrementjavascript.md)