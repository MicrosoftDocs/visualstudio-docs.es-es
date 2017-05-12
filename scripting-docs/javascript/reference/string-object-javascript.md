---
title: "String (Objeto de JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "String_JavaScript"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "String (objeto)"
  - "String (objeto), información general"
ms.assetid: 8063ecd5-5778-4e87-b985-b21420171914
caps.latest.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 32
---
# String (Objeto de JavaScript)
Permite manipular y dar formato a cadenas de texto y determinar y ubicar subcadenas dentro de cadenas.  
  
## Sintaxis  
  
```  
  
newString = new String(["stringLiteral"])  
```  
  
## Parámetros  
 `newString`  
 Obligatorio.  Nombre de variable a la que se asigna el objeto `String`.  
  
 `stringLiteral`  
 Opcional.  Cualquier grupo de caracteres Unicode.  
  
## Comentarios  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] proporciona secuencias de escape que se pueden incluir en cadenas para crear caracteres que no es posible escribir directamente.  Por ejemplo, `\t` especifica un carácter de tabulación.  Para obtener más información, consulte [Caracteres especiales](../../javascript/advanced/special-characters-javascript.md).  
  
## Literales de cadena  
 Un *literal de cadena* está compuesto por cero o más caracteres entre comillas simples o dobles.  Un literal de cadena tiene un tipo de datos principal \(primitivo\) de `string`.  Un *objeto String* se crea mediante el [operador new](../../javascript/reference/new-operator-decrementjavascript.md) y tiene un tipo de datos `Object`.  
  
 En el ejemplo siguiente se muestra que el tipo de datos de un literal de cadena no es igual que el de un objeto `String`.  
  
```javascript  
var strLit = "This is a string literal.";  
var strObj = new String("This is a string object.");  
  
document.write(typeof strLit);  
document.write("<br/>");  
document.write(typeof strObj);  
// Output:  
// string  
// object  
```  
  
## Métodos para literales de cadena  
 Al llamar a un método en un literal de cadena, se convierte temporalmente en un objeto contenedor de la cadena.  El literal de cadena se trata como si se usara el operador `new` para crearlo.  
  
 En el ejemplo siguiente se aplica el método `toUpperCase` a un literal de cadena.  
  
```javascript  
var strLit = "This is a string literal.";  
  
var result1 = strLit.toUpperCase();  
  
var result2 = (new String(strLit)).toUpperCase();  
  
document.write(result1);  
document.write("<br/>");  
document.write(result2);  
// Output:   
// THIS IS A STRING LITERAL.  
// THIS IS A STRING LITERAL.  
```  
  
## Tener acceso a un carácter individual  
 Puede tener acceso a un único carácter de una cadena como una propiedad indizada de matriz de solo lectura.  Esta característica se presentó por primera vez en [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)].  En el ejemplo siguiente se tiene acceso a caracteres individuales de una cadena.  
  
```javascript  
var str = "abcd";  
var result = str[2];  
document.write (result);  
// Output: c  
  
var result = "the"[0];  
document.write(result);  
// Output: t  
```  
  
## Requisitos  
 `String Object` se presentó por primera vez en [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)].  Algunos miembros de las listas siguientes se presentaron en versiones posteriores.  
  
<a name="js56jsobjstringprop"></a>   
## Propiedades  
 En la tabla siguiente se muestran las propiedades del objeto `String`.  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|[constructor \(Propiedad\)](../../javascript/reference/constructor-property-string.md)|Especifica la función que crea un objeto.|  
|[length \(Propiedad, String\)](../../javascript/reference/length-property-string-javascript.md)|Devuelve la longitud de un objeto `String`.|  
|[prototype \(Propiedad\)](../../javascript/reference/prototype-property-string.md)|Devuelve una referencia al prototipo correspondiente a una clase de objetos.|  
  
## Funciones  
 En la tabla siguiente se muestran las funciones del objeto `String`.  
  
|Función|Descripción|  
|-------------|-----------------|  
|[Función String.fromCharCode](../../javascript/reference/string-fromcharcode-function-javascript.md)|Devuelve una cadena a partir de varios valores de caracteres Unicode.|  
|[Función String.fromCodePoint](../../javascript/reference/string-fromcodepoint-function-javascript.md)|Devuelve la cadena asociada a un punto de código Unicode UTF\-16.|  
|[Función String.raw](../../javascript/reference/string-raw-function-javascript.md)|Devuelve el formato de cadena sin formato de una cadena de plantilla.|  
  
<a name="js56jsobjstringmeth"></a>   
## Métodos  
 En la tabla siguiente se muestran los métodos del objeto `String`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[anchor \(Método\)](../../javascript/reference/html-tag-methods-javascript.md)|Coloca un delimitador HTML que tiene un atributo NAME a ambos lados del texto.|  
|[big \(Método\)](../../javascript/reference/html-tag-methods-javascript.md)|Coloca etiquetas HTML \<BIG\> a ambos lados del texto.|  
|[blink \(Método\)](../../javascript/reference/html-tag-methods-javascript.md)|Coloca etiquetas HTML \<BLINK\> a ambos lados del texto.|  
|[bold \(Método\)](../../javascript/reference/html-tag-methods-javascript.md)|Coloca etiquetas HTML \<B\> a ambos lados del texto.|  
|[charAt \(Método\)](../../javascript/reference/charat-method-string-javascript.md)|Devuelve el carácter que se encuentra en el índice especificado.|  
|[charCodeAt \(Método\)](../../javascript/reference/charcodeat-method-string-javascript.md)|Devuelve la codificación Unicode del carácter que se especifique.|  
|[codePointAt \(Método\)](../../javascript/reference/codepointat-method-string-javascript.md)|Devuelve el punto de código de un carácter Unicode UTF\-16.|  
|[concat \(Método, String\)](../../javascript/reference/concat-method-string-javascript.md)|Devuelve una cadena que contiene la concatenación de las dos cadenas proporcionadas.|  
|[EndsWith \(Método\)](../../javascript/reference/endswith-method-string-javascript.md)|Devuelve un valor booleano que indica si una cadena o subcadena acaba con la cadena pasada.|  
|[includes \(Método\)](../../javascript/reference/includes-method-string-javascript.md)|Devuelve un valor booleano que indica si la cadena pasada se encuentra en el objeto de cadena.|  
|[fixed \(Método\)](../../javascript/reference/html-tag-methods-javascript.md)|Coloca etiquetas HTML \<TT\> a ambos lados del texto.|  
|[fontcolor \(Método\)](../../javascript/reference/html-tag-methods-javascript.md)|Coloca etiquetas HTML \<FONT\> con un atributo COLOR a ambos lados del texto.|  
|[fontsize \(Método\)](../../javascript/reference/html-tag-methods-javascript.md)|Coloca etiquetas HTML \<FONT\> con un atributo SIZE alrededor del texto.|  
|[hasOwnProperty \(Método\)](../../javascript/reference/hasownproperty-method-object-javascript.md)|Devuelve un valor booleano que indica si un objeto tiene una propiedad con el nombre especificado.|  
|[indexOf \(Método, String\)](../../javascript/reference/indexof-method-string-javascript.md)|Devuelve la posición del carácter donde tiene lugar la primera repetición de una subcadena dentro de una cadena.|  
|[isPrototypeOf \(Método\)](../../javascript/reference/isprototypeof-method-object-javascript.md)|Devuelve un valor booleano que indica si un objeto existe en la cadena de prototipo de otro objeto.|  
|[italics \(Método\)](../../javascript/reference/html-tag-methods-javascript.md)|Coloca etiquetas HTML \<I\> a ambos lados del texto.|  
|[lastIndexOf \(Método, String\)](../../javascript/reference/lastindexof-method-string-javascript.md)|Devuelve la última repetición de una subcadena dentro de una cadena.|  
|[link \(Método\)](../../javascript/reference/html-tag-methods-javascript.md)|Coloca un delimitador HTML que tiene un atributo HREF a ambos lados del texto.|  
|[localeCompare \(Método\)](../../javascript/reference/localecompare-method-string-javascript.md)|Devuelve un valor que indica si dos cadenas son equivalentes en la configuración regional actual.|  
|[match \(Método\)](../../javascript/reference/match-method-string-javascript.md)|Busca una cadena mediante un objeto **Regular Expression** proporcionado y devuelve los resultados como una matriz.|  
|[normalize \(Método\)](../../javascript/reference/normalize-method-string-javascript.md)|Devuelve la forma de normalización Unicode de una cadena especificada.|  
|[propertyIsEnumerable \(Método\)](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Devuelve un valor booleano que indica si una propiedad especificada forma parte de un objeto y si se puede enumerar.|  
|[repeat \(Método\)](../../javascript/reference/repeat-method-string-javascript.md)|Devuelve un nuevo objeto de cadena con un valor igual a la cadena original repetido el número de veces especificado.|  
|[replace \(Método\)](../../javascript/reference/replace-method-string-javascript.md)|Usa una expresión regular para reemplazar texto en una cadena y devuelve el resultado.|  
|[search \(Método\)](../../javascript/reference/search-method-string-javascript.md)|Devuelve la posición de la primera coincidencia de subcadena en una búsqueda de expresión regular.|  
|[slice \(Método, String\)](../../javascript/reference/slice-method-string-javascript.md)|Devuelve una sección de una cadena.|  
|[small \(Método\)](../../javascript/reference/html-tag-methods-javascript.md)|Coloca etiquetas HTML \<SMALL\> a ambos lados del texto.|  
|[split \(Método\)](../../javascript/reference/split-method-string-javascript.md)|Devuelve la matriz de cadenas resultante de la separación de una cadena en subcadenas.|  
|[startsWith \(Método\)](../../javascript/reference/startswith-method-string-javascript.md)|Devuelve un valor booleano que indica si una cadena o subcadena empieza con la cadena pasada.|  
|[strike \(Método\)](../../javascript/reference/html-tag-methods-javascript.md)|Coloca etiquetas HTML \<STRIKE\> a ambos lados del texto.|  
|[sub \(Método\)](../../javascript/reference/html-tag-methods-javascript.md)|Coloca etiquetas HTML \<SUB\> a ambos lados del texto.|  
|[substr \(Método\)](../../javascript/reference/substr-method-string-javascript.md)|Devuelve una subcadena que comienza en una posición especificada y tiene una longitud especificada.|  
|[substring \(Método\)](../../javascript/reference/substring-method-string-javascript.md)|Devuelve la subcadena en la ubicación especificada dentro de un objeto `String`.|  
|[sup \(Método\)](../../javascript/reference/html-tag-methods-javascript.md)|Coloca etiquetas HTML \<SUP\> a ambos lados del texto.|  
|[toLocaleLowerCase \(Método\)](../../javascript/reference/tolocalelowercase-method-string-javascript.md)|Devuelve una cadena en la que todos los caracteres alfabéticos se convierten a minúsculas, según la configuración regional actual del entorno de host.|  
|[toLocaleString \(Método\)](../../javascript/reference/tolocalestring-method-object-javascript.md)|Devuelve un objeto convertido en cadena usando la configuración regional actual.|  
|[toLocaleUpperCase \(Método\)](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)|Devuelve una cadena en la que todos los caracteres alfabéticos se convierten a mayúsculas, según la configuración regional actual del entorno de host.|  
|[toLowerCase \(Método\)](../../javascript/reference/tolowercase-method-javascript.md)|Devuelve una cadena en la que todos los caracteres alfabéticos se convierten a minúsculas.|  
|[toString \(Método\)](../../javascript/reference/tostring-method-string-1.md)|Devuelve la cadena.|  
|[toUpperCase \(Método\)](../../javascript/reference/touppercase-method-string-javascript.md)|Devuelve una cadena en la que todos los caracteres alfabéticos se convierten a mayúsculas.|  
|[trim \(Método\)](../../javascript/reference/trim-method-string-javascript.md)|Devuelve una cadena donde se han quitado los caracteres de espacio en blanco iniciales y finales y los caracteres de terminador de línea.|  
|[valueOf \(Método\)](../../javascript/reference/valueof-method-string.md)|Devuelve la cadena.|  
  
## Vea también  
 [new \(Operador\)](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Aplicación de ejemplo de desplazamiento, panorámica y zoom](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)