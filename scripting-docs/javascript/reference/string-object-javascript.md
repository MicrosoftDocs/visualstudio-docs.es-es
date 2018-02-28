---
title: String (objeto de JavaScript) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- String_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- String object
- String object, overview
ms.assetid: 8063ecd5-5778-4e87-b985-b21420171914
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d58f567bb301b29324fee8ed75fc95fd1a4791ea
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="string-object-javascript"></a>String (Objeto de JavaScript)
Permite manipular y dar formato a cadenas de texto y determinar y ubicar subcadenas dentro de cadenas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
newString = new String(["stringLiteral"])  
```  
  
## <a name="parameters"></a>Parámetros  
 `newString`  
 Obligatorio. Nombre de variable a la que se asigna el objeto `String`.  
  
 `stringLiteral`  
 Opcional. Cualquier grupo de caracteres Unicode.  
  
## <a name="remarks"></a>Comentarios  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] proporciona secuencias de escape que se pueden incluir en cadenas para crear caracteres que no es posible escribir directamente. Por ejemplo, `\t` especifica un carácter de tabulación. Para obtener más información, consulte [Caracteres especiales](../../javascript/advanced/special-characters-javascript.md).  
  
## <a name="string-literals"></a>Literales de cadena  
 A *literal de cadena* es cero o más caracteres entre comillas simples o dobles. Un literal de cadena tiene un tipo de datos principal (primitivo) de `string`. A *String (objeto)* se crea mediante la [new (operador)](../../javascript/reference/new-operator-decrementjavascript.md), y tiene un tipo de datos de `Object`.  
  
 En el ejemplo siguiente se muestra que el tipo de datos de un literal de cadena no es igual que el de un objeto `String`.  
  
```JavaScript  
var strLit = "This is a string literal.";  
var strObj = new String("This is a string object.");  
  
document.write(typeof strLit);  
document.write("<br/>");  
document.write(typeof strObj);  
// Output:  
// string  
// object  
```  
  
## <a name="methods-for-string-literals"></a>Métodos para literales de cadena  
 Al llamar a un método en un literal de cadena, se convierte temporalmente en un objeto contenedor de la cadena. El literal de cadena se trata como si se usara el operador `new` para crearlo.  
  
 En el ejemplo siguiente se aplica el método `toUpperCase` a un literal de cadena.  
  
```JavaScript  
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
  
## <a name="accessing-an-individual-character"></a>Tener acceso a un carácter individual  
 Puede tener acceso a un único carácter de una cadena como una propiedad indizada de matriz de solo lectura. Esta característica se presentó por primera vez en [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)]. En el ejemplo siguiente se tiene acceso a caracteres individuales de una cadena.  
  
```JavaScript  
var str = "abcd";  
var result = str[2];  
document.write (result);  
// Output: c  
  
var result = "the"[0];  
document.write(result);  
// Output: t  
```  
  
## <a name="requirements"></a>Requisitos  
 `String Object` se presentó por primera vez en [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)]. Algunos miembros de las listas siguientes se presentaron en versiones posteriores.  
  
<a name="js56jsobjstringprop"></a>   
## <a name="properties"></a>Propiedades  
 En la tabla siguiente se muestran las propiedades del objeto `String`.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|[constructor (propiedad)](../../javascript/reference/constructor-property-string.md)|Especifica la función que crea un objeto.|  
|[length (Propiedad, String)](../../javascript/reference/length-property-string-javascript.md)|Devuelve la longitud de un objeto `String`.|  
|[prototype (propiedad)](../../javascript/reference/prototype-property-string.md)|Devuelve una referencia al prototipo correspondiente a una clase de objetos.|  
  
## <a name="functions"></a>Funciones  
 En la tabla siguiente se muestran las funciones del objeto `String`.  
  
|Función|Descripción|  
|--------------|-----------------|  
|[String.fromCharCode (Función)](../../javascript/reference/string-fromcharcode-function-javascript.md)|Devuelve una cadena a partir de varios valores de caracteres Unicode.|  
|[String.fromCodePoint (Función)](../../javascript/reference/string-fromcodepoint-function-javascript.md)|Devuelve la cadena asociada a un punto de código Unicode UTF-16.|  
|[String.raw (Función)](../../javascript/reference/string-raw-function-javascript.md)|Devuelve la forma de cadena sin formato de una cadena de plantilla.|  
  
<a name="js56jsobjstringmeth"></a>   
## <a name="methods"></a>Métodos  
 En la tabla siguiente se muestran los métodos del objeto `String`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Anchor (método)](../../javascript/reference/html-tag-methods-javascript.md)|Coloca un delimitador HTML que tiene un atributo NAME a ambos lados del texto.|  
|[big (método)](../../javascript/reference/html-tag-methods-javascript.md)|Coloca HTML \<BIG > etiquetas alrededor del texto.|  
|[blink (Método)](../../javascript/reference/html-tag-methods-javascript.md)|Coloca HTML \<BLINK > etiquetas alrededor del texto.|  
|[bold (Método)](../../javascript/reference/html-tag-methods-javascript.md)|Coloca HTML \<B > etiquetas alrededor del texto.|  
|[charAt (Método)](../../javascript/reference/charat-method-string-javascript.md)|Devuelve el carácter que se encuentra en el índice especificado.|  
|[charCodeAt (Método)](../../javascript/reference/charcodeat-method-string-javascript.md)|Devuelve la codificación Unicode del carácter que se especifique.|  
|[codePointAt (método)](../../javascript/reference/codepointat-method-string-javascript.md)|Devuelve el punto de código de un carácter Unicode UTF-16.|  
|[concat (Método, String)](../../javascript/reference/concat-method-string-javascript.md)|Devuelve una cadena que contiene la concatenación de las dos cadenas proporcionadas.|  
|[endsWith (método)](../../javascript/reference/endswith-method-string-javascript.md)|Devuelve un valor booleano que indica si una cadena o subcadena acaba con la cadena pasada.|  
|[includes (método)](../../javascript/reference/includes-method-string-javascript.md)|Devuelve un valor booleano que indica si la cadena pasada se encuentra en el objeto de cadena.|  
|[fixed (Método)](../../javascript/reference/html-tag-methods-javascript.md)|Coloca HTML \<TT > etiquetas alrededor del texto.|  
|[fontcolor (Método)](../../javascript/reference/html-tag-methods-javascript.md)|Coloca HTML \<fuente > etiquetas con un atributo COLOR a ambos lados del texto.|  
|[fontsize (Método)](../../javascript/reference/html-tag-methods-javascript.md)|Coloca HTML \<fuente > etiquetas con un atributo SIZE alrededor del texto.|  
|[hasOwnProperty (Método)](../../javascript/reference/hasownproperty-method-object-javascript.md)|Devuelve un valor booleano que indica si un objeto tiene una propiedad con el nombre especificado.|  
|[indexOf (Método, String)](../../javascript/reference/indexof-method-string-javascript.md)|Devuelve la posición del carácter donde tiene lugar la primera repetición de una subcadena dentro de una cadena.|  
|[isPrototypeOf (método)](../../javascript/reference/isprototypeof-method-object-javascript.md)|Devuelve un valor booleano que indica si un objeto existe en la cadena de prototipo de otro objeto.|  
|[italics (Método)](../../javascript/reference/html-tag-methods-javascript.md)|Coloca HTML \<I > etiquetas alrededor del texto.|  
|[lastIndexOf (Método, String)](../../javascript/reference/lastindexof-method-string-javascript.md)|Devuelve la última repetición de una subcadena dentro de una cadena.|  
|[link (Método)](../../javascript/reference/html-tag-methods-javascript.md)|Coloca un delimitador HTML que tiene un atributo HREF a ambos lados del texto.|  
|[localeCompare (Método)](../../javascript/reference/localecompare-method-string-javascript.md)|Devuelve un valor que indica si dos cadenas son equivalentes en la configuración regional actual.|  
|[match (Método)](../../javascript/reference/match-method-string-javascript.md)|Busca una cadena mediante el uso de un proporcionado **expresión Regular** de objetos y devuelve los resultados como una matriz.|  
|[Método Normalize](../../javascript/reference/normalize-method-string-javascript.md)|Devuelve la forma de normalización Unicode de una cadena especificada.|  
|[propertyIsEnumerable (Método)](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Devuelve un valor booleano que indica si una propiedad especificada forma parte de un objeto y si se puede enumerar.|  
|[Método Repeat](../../javascript/reference/repeat-method-string-javascript.md)|Devuelve un nuevo objeto de cadena con un valor igual a la cadena original repetido el número de veces especificado.|  
|[replace (Método)](../../javascript/reference/replace-method-string-javascript.md)|Usa una expresión regular para reemplazar texto en una cadena y devuelve el resultado.|  
|[search (Método)](../../javascript/reference/search-method-string-javascript.md)|Devuelve la posición de la primera coincidencia de subcadena en una búsqueda de expresión regular.|  
|[slice (Método, String)](../../javascript/reference/slice-method-string-javascript.md)|Devuelve una sección de una cadena.|  
|[small (Método)](../../javascript/reference/html-tag-methods-javascript.md)|Coloca HTML \<pequeño > etiquetas alrededor del texto.|  
|[split (Método)](../../javascript/reference/split-method-string-javascript.md)|Devuelve la matriz de cadenas resultante de la separación de una cadena en subcadenas.|  
|[startsWith (método)](../../javascript/reference/startswith-method-string-javascript.md)|Devuelve un valor booleano que indica si una cadena o subcadena empieza con la cadena pasada.|  
|[strike (Método)](../../javascript/reference/html-tag-methods-javascript.md)|Coloca HTML \<STRIKE > etiquetas alrededor del texto.|  
|[sub (Método)](../../javascript/reference/html-tag-methods-javascript.md)|Coloca HTML \<SUB > etiquetas alrededor del texto.|  
|[substr (Método)](../../javascript/reference/substr-method-string-javascript.md)|Devuelve una subcadena que comienza en una posición especificada y tiene una longitud especificada.|  
|[substring (Método)](../../javascript/reference/substring-method-string-javascript.md)|Devuelve la subcadena en la ubicación especificada dentro de un objeto `String`.|  
|[sup (Método)](../../javascript/reference/html-tag-methods-javascript.md)|Coloca HTML \<SUP > etiquetas alrededor del texto.|  
|[toLocaleLowerCase (método)](../../javascript/reference/tolocalelowercase-method-string-javascript.md)|Devuelve una cadena en la que todos los caracteres alfabéticos se convierten a minúsculas, según la configuración regional actual del entorno de host.|  
|[toLocaleString (Método)](../../javascript/reference/tolocalestring-method-object-javascript.md)|Devuelve un objeto convertido en cadena usando la configuración regional actual.|  
|[toLocaleUpperCase (método)](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)|Devuelve una cadena en la que todos los caracteres alfabéticos se convierten a mayúsculas, según la configuración regional actual del entorno de host.|  
|[toLowerCase (Método)](../../javascript/reference/tolowercase-method-javascript.md)|Devuelve una cadena en la que todos los caracteres alfabéticos se convierten a minúsculas.|  
|[toString (método)](../../javascript/reference/tostring-method-string-1.md)|Devuelve la cadena.|  
|[toUpperCase (Método)](../../javascript/reference/touppercase-method-string-javascript.md)|Devuelve una cadena en la que todos los caracteres alfabéticos se convierten a mayúsculas.|  
|[trim (Método)](../../javascript/reference/trim-method-string-javascript.md)|Devuelve una cadena donde se han quitado los caracteres de espacio en blanco iniciales y finales y los caracteres de terminador de línea.|  
|[valueOf (método)](../../javascript/reference/valueof-method-string.md)|Devuelve la cadena.|  
  
## <a name="see-also"></a>Vea también  
 [new (Operador, Referencia de C#)](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Aplicación de ejemplo de desplazamiento, panorámica y zoom](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)