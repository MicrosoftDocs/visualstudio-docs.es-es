---
title: "Tipos de datos (JavaScript) | Microsoft Docs"
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
  - "Boolean (tipo de datos), tipos de datos admitidos"
ms.assetid: c7a6bd3a-4b1c-4dbe-8505-106dbf483b41
caps.latest.revision: 35
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 35
---
# Tipos de datos (JavaScript)
En [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], hay tres tipos de datos principales, dos tipos de datos compuestos y dos tipos de datos especiales.  
  
## Tipos de datos principales  
 Los tipos de datos principales \(primitivos\) son:  
  
-   Cadena.  
  
-   Número  
  
-   Boolean  
  
## Tipos de datos compuestos  
 Los tipos de datos compuestos \(de referencia\) son:  
  
-   Objeto.  
  
-   Matriz  
  
## Tipos de datos especiales  
 Los tipos de datos especiales son:  
  
-   Null  
  
-   No definido  
  
## String \(Tipo de datos\)  
 Un valor de cadena está formado por una cadena de cero o más caracteres Unicode \(letras, dígitos y signos de puntuación\).  El tipo de datos string se usa para representar texto en [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  Incluya literales de cadena en los scripts, encerrándolos entre pares de comillas sencillas o dobles.  Pueden incluirse comillas dobles en cadenas delimitadas por comillas simples y viceversa.  A continuación se incluyen ejemplos de cadenas:  
  
```javascript  
"Happy am I; from care I'm free!"  
'"Avast, ye lubbers!" roared the technician.'   
"45"  
'c'  
```  
  
 Observe que [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] no tiene un tipo para representar un solo carácter.  Para representar un único carácter en [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], cree una cadena que conste de un solo carácter.  Las cadenas que no contienen ningún carácter \(""\) se denominan cadenas vacías \(de longitud cero\).  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] proporciona secuencias de escape que se pueden incluir en cadenas para crear caracteres que no es posible escribir directamente.  Por ejemplo, `\t` especifica un carácter de tabulación.  Para obtener más información, vea [Caracteres especiales](../javascript/advanced/special-characters-javascript.md).  
  
## Number \(Tipo de datos\)  
 En [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], no se distingue entre los valores enteros y de punto flotante; un número de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] puede ser cualquiera de ellos \(internamente, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] representa todos los números como valores de punto flotante\).  
  
### Valores enteros  
 Los valores enteros pueden ser números enteros positivos, números enteros negativos y 0.  Se pueden representar en base 10 \(decimal\), base 16 \(hexadecimal\) y base 8 \(octal\).  La mayor parte de los números de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] se escriben en decimal.  
  
 Para indicar enteros hexadecimales \("hex"\), ponga como prefijo "0x" \(cero y x o X\).  Sólo pueden contener dígitos del 0 al 9 y letras de la A a la F \(mayúsculas o minúsculas\).  Las letras comprendidas entre la A y la F se usan para representar, como dígitos únicos, los números comprendidos entre 10 y 15 en base 10.  Es decir, 0xF es equivalente a 15 y 0x10 es equivalente a 16.  
  
 Para denotar enteros octales, ponga como prefijo un "0" \(cero\) inicial.  Sólo pueden contener dígitos del 0 al 7.  Un número precedido por un "0" y que contiene los dígitos "8" y\/o "9" se interpreta como un número decimal.  
  
 Los números hexadecimales y octales pueden ser negativos, pero no pueden contener una parte decimal ni escribirse en notación científica \(exponencial\).  
  
> [!NOTE]
>  A partir de [!INCLUDE[jsv9text](../javascript/includes/jsv9text-md.md)], la [función parseInt](../javascript/reference/parseint-function-javascript.md) no trata como octal una cadena que tiene un prefijo "0".  Sin embargo, cuando no se usa la función `parseInt`, las cadenas con un prefijo "0" todavía se pueden interpretar como octales.  
  
### Valores de punto flotante  
 Los valores de punto flotante pueden ser números enteros con una parte decimal.  Además, pueden expresarse en notación científica.  Es decir, se usa una "e" en mayúsculas o minúsculas para representar "diez a la potencia de".  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] representa los números usando el estándar de punto flotante de ocho bytes de IEEE 754 para la representación numérica.  Esto significa que puede escribir números tan grandes como 1,79769x10<sup>308</sup> y tan pequeños como 5x10<sup>-324</sup>.  Un número que contiene un separador decimal y que tiene un solo "0" delante del separador decimal se interpreta como un número de punto flotante decimal.  
  
 Tenga en cuenta que un número que comience con "0x" o "00" y contenga un separador decimal generará un error.  A continuación se incluyen algunos ejemplos de números de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
|Número|Descripción|Equivalente decimal|  
|------------|-----------------|-------------------------|  
|,0001, 0,0001, 1e\-4, 1,0e\-4|Cuatro números de punto flotante equivalentes.|0.0001|  
|3,45e2|Número en punto flotante.|345|  
|45|Entero.|45|  
|0378|Entero.  Aunque parece un número octal \(comienza con un cero\), 8 no es un dígito octal válido, por lo que el número se interpretará como un decimal.|378|  
|0377|Entero octal.  Observe que aunque en apariencia se trata del número precedente al anterior, su valor real es muy diferente.|255|  
|0.0001|Número de punto flotante.  Aunque este número comienza con un cero, no es octal, ya que tiene un separador decimal.|0.0001|  
|00.0001|Esto es un error.  Los dos ceros iniciales marcan el número como octal, pero los octales no permiten un componente decimal.|N\/D \(error del compilador\)|  
|0Xff|Entero hexadecimal.|255|  
|0x37CF|Entero hexadecimal.|14287|  
|0x3e7|Entero hexadecimal.  Observe que la 'e' no se interpreta como exponenciación.|999|  
|0x3,45e2|Esto es un error.  Los números hexadecimales no pueden tener partes decimales.|N\/D \(error del compilador\)|  
  
 Además, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] contiene números con valores especiales.  Estos son:  
  
-   NaN \(no es un número\).  Se utiliza al realizar una operación matemática en datos inapropiados, como cadenas o con el valor no definido  
  
-   Infinito positivo.  Se utiliza cuando un número positivo es demasiado grande para representarlo en [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]  
  
-   Infinito negativo.  Se usa cuando un número negativo es demasiado grande para representarlo en [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]  
  
-   Cero negativo y positivo.  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] distingue entre cero positivo y negativo.  
  
## Tipo de datos booleano  
 Mientras que los tipos de datos de cadena y número pueden tener un número prácticamente ilimitado de valores diferentes, el tipo de datos booleano sólo puede tener dos:  Estos son los literales `true` y `false`.  Un valor booleano es un valor de validez: especifica si la condición es verdadera o no.  
  
 Las comparaciones realizadas en los scripts siempre tienen un resultado booleano.  Observe la línea siguiente de código de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```javascript  
y = (x == 2000);  
```  
  
 Aquí, el valor de la variable `x` se compara con el número 2000.  Si lo es, el resultado de la comparación es el valor booleano **true**, que se asigna a la variable `y`.  Si `x` no es igual a 2000, el resultado de la comparación es el valor booleano `false`.  
  
 Los valores booleanos son especialmente útiles en estructuras de control.  El código siguiente combina una comparación que crea un valor booleano directamente con una instrucción que la usa.  Observe el siguiente código de ejemplo de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```javascript  
if (x == 2000) {  
    z = z + 1;  
}  
else {  
    x = x + 1;  
}  
```  
  
 La instrucción `if/else` de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] realiza una acción si un valor booleano es `true` \(`z = z + 1`\) y realiza una acción alternativa si el valor booleano es `false` \(`x = x + 1`\).  
  
 Puede usar cualquier expresión como expresión comparativa.  Se interpreta como `false` cualquier expresión que se evalúa como 0, NULL, sin definir o cadena vacía.  Se interpreta como `true` cualquier expresión que se evalúa como cualquier otro valor.  Por ejemplo, podría utilizar una expresión como:  
  
```javascript  
// This may not do what you expect. See below!  
if (x = y + z)   
```  
  
 Observe que en la línea anterior no se comprueba si `x` es igual a `y + z`, ya que la sintaxis utiliza únicamente un signo igual \(operador de asignaciones\).  En su lugar, el código anterior asigna el valor de `y + z` a la variable `x` y luego comprueba si el resultado de toda la expresión \(el valor de `x`\) es cero.  Para comprobar si `x` es igual a `y + z`, debe usar el código siguiente.  
  
```javascript  
// This is different from the code above!  
if (x == y + z)   
```  
  
 Para obtener más información acerca de las comparaciones, vea [Controlar el flujo del programa](../javascript/controlling-program-flow-javascript.md).  
  
## El tipo de datos NULL  
 El tipo de datos `null` solo tiene un valor en [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]: null.  La palabra clave `null` no se puede usar como nombre de función ni de variable.  
  
 Una variable que contiene `null` no contiene ningún número, cadena, valor booleano, matriz u objeto.  Para borrar el contenido de una variable \(sin eliminar la variable\), asígnele el valor `null`.  
  
 Observe que en [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], `null` no es lo mismo que 0 \(como en C y C\+\+\).  Asimismo, observe que el operador `typeof` de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] interpreta los valores `null` como un tipo `Object`, no como un tipo `null`.  Este comportamiento, que puede provocar confusiones, se mantiene por compatibilidad con versiones anteriores.  
  
## El tipo de datos undefined  
 Se devuelve el valor `undefined` cuando se usa una propiedad de objeto que no existe o una variable que se ha declarado, pero nunca ha tenido un valor asignado.  
  
 puede comprobar si una variable existe comparándola con `undefined`, aunque puede comprobar si su tipo es `undefined` si compara el tipo de la variable con la cadena “undefined”.  En el ejemplo siguiente se muestra cómo averiguar si se ha declarado la variable `x`:  
  
```javascript  
  
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
  
 También puede comparar el valor no definido en `null`.  Esta comparación es `true` si la propiedad `someObject.prop` es `null` o si la propiedad `someObject.prop` no existe.  
  
```javascript  
someObject.prop == null;  
```  
  
 Para averiguar si existe una propiedad de objeto, puede usar el operador **in**:  
  
```javascript  
if ("prop" in someObject)  
    // someObject has the property 'prop'  
```  
  
## Vea también  
 [Objetos y matrices](../javascript/objects-and-arrays-javascript.md)   
 [typeof \(Operador\)](../javascript/reference/typeof-operator-decrementjavascript.md)