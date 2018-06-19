---
title: JSON.stringify (función) (JavaScript) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- stringify method
ms.assetid: 0fafaf3b-c29b-46dc-b65b-ca223064a1d0
caps.latest.revision: 40
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3539bb003ed20a3ff7586e42466bf7c47165b83f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640565"
---
# <a name="jsonstringify-function-javascript"></a>JSON.stringify (Función de JavaScript)
Convierte un valor de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] en una cadena de la notación de objetos JavaScript (JSON).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
JSON.stringify(  
value [, replacer] [, space])  
```  
  
## <a name="parameters"></a>Parámetros  
 `value`  
 Requerido. Valor de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], normalmente un objeto o una matriz, que se va a convertir.  
  
 `replacer`  
 Opcional. Función o matriz que transforma los resultados.  
  
 Si `replacer` es una función, `JSON.stringify` llama a la función y pasa la clave y el valor de cada miembro. El valor devuelto se utiliza en lugar del valor original. Si la función devuelve `undefined`, el miembro se excluye. La clave del objeto raíz es una cadena vacía: "".  
  
 Si `replacer` es una matriz, solo se convierten los miembros de la matriz que tienen valores de clave. El orden en que se convierten los miembros es el mismo que el de las claves de la matriz. La matriz `replacer` se omite cuando el argumento `value` también es una matriz.  
  
 `space`  
 Opcional. Agrega sangría, espacio en blanco y caracteres de salto de línea al texto JSON del valor devuelto, para que sea más fácil de leer.  
  
 Si se omite `space`, el texto del valor devuelto se genera sin ningún espacio en blanco adicional.  
  
 Si `space` es un número, se aplica al texto del valor devuelto una sangría con el número especificado de espacios en blanco en cada nivel. Si `space` es mayor que 10, la sangría aplicada al texto es de 10 espacios.  
  
 Si `space` es una cadena no vacía, como '\t', al texto del valor devuelto se le aplica una sangría con los caracteres de la cadena en cada nivel.  
  
 Si `space` es una cadena de más de 10 caracteres, se utilizan los diez primeros.  
  
## <a name="return-value"></a>Valor devuelto  
 Cadena que contiene el texto JSON.  
  
## <a name="exceptions"></a>Excepciones  
  
|Excepción|Condición|  
|---------------|---------------|  
|[Argumento reemplazante no válido](../../javascript/misc/invalid-replacer-argument.md)|El argumento `replacer` no es una función ni una matriz.|  
|[Referencia circular en un argumento de valor no admitida](../../javascript/misc/circular-reference-in-value-argument-not-supported.md)|El argumento `value` contiene una referencia circular.|  
  
## <a name="remarks"></a>Comentarios  
 Si `value` tiene un método `toJSON`, la función `JSON.stringify` usa el valor devuelto de ese método. Si el valor devuelto del método `toJSON` es `undefined`, el miembro no se convierte. Esto permite que un objeto determine su propia representación JSON.  
  
 Los valores que no tienen representaciones JSON, como `undefined`, no se convierten. En los objetos, se quitan. En las matrices, se reemplazan con null.  
  
 Los valores de cadena comienzan y finalizan con una comilla. Todos los caracteres Unicode se pueden agregar entre comillas, salvo los caracteres que se deben especificar con una barra diagonal inversa. Los caracteres siguientes deben ir precedidos de una barra diagonal inversa:  
  
-   Marca de comillas dobles (").  
  
-   Barra diagonal inversa (\\)  
  
-   Retroceso (b)  
  
-   Avance de página (f)  
  
-   Nueva línea (n)  
  
-   Retorno de carro (r)  
  
-   Tabulación horizontal (t)  
  
-   Cuatro dígitos hexadecimales (uhhhh)  
  
## <a name="order-of-execution"></a>Orden de ejecución  
 Durante el proceso de serialización, si hay un método `toJSON` para el argumento `value`, `JSON.stringify` llama primero al método `toJSON`. Si no lo hay, se usa el valor original. A continuación, si se proporciona un argumento `replacer`, el valor (original o devuelto de `toJSON`) se reemplaza con el valor devuelto del argumento `replacer`. Por último, se agregan espacios en blanco al valor de acuerdo con el argumento `space` opcional para generar el texto JSON definitivo.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se usa `JSON.stringify` para convertir el objeto `contact` en texto JSON. La matriz `memberfilter` se define de forma que solo se conviertan los miembros `surname` y `phone`. El miembro `firstname` se omite.  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Array();  
memberfilter[0] = "surname";  
memberfilter[1] = "phone";  
var jsonText = JSON.stringify(contact, memberfilter, "\t");  
document.write(jsonText);  
// Output:   
// { "surname": "Aaberg", "phone": [ "555-0100", "555-0120" ] }  
```  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se usa `JSON.stringify` con una matriz. La función `replaceToUpper` convierte todas las cadenas de la matriz a mayúsculas.  
  
```JavaScript  
var continents = new Array();  
continents[0] = "Europe";  
continents[1] = "Asia";  
continents[2] = "Australia";  
continents[3] = "Antarctica";  
continents[4] = "North America";  
continents[5] = "South America";  
continents[6] = "Africa";  
  
var jsonText = JSON.stringify(continents, replaceToUpper);  
  
function replaceToUpper(key, value) {  
    return value.toString().toUpperCase();  
}  
  
//Output:  
// "EUROPE,ASIA,AUSTRALIA,ANTARCTICA,NORTH AMERICA,SOUTH AMERICA,AFRICA"  
  
```  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se usa el método `toJSON` para convertir los valores alfanuméricos a mayúsculas.  
  
```JavaScript  
var contact = new Object();   
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
contact.toJSON = function(key)  
 {  
    var replacement = new Object();  
    for (var val in this)  
    {  
        if (typeof (this[val]) === 'string')  
            replacement[val] = this[val].toUpperCase();  
        else  
            replacement[val] = this[val]  
    }  
    return replacement;  
};  
  
var jsonText = JSON.stringify(contact);  
document.write(jsonText);  
  
// Output:  
{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}  
  
'{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}'  
*/  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [JSON.parse (función)](../../javascript/reference/json-parse-function-javascript.md)   
 [toJSON (método, Date)](../../javascript/reference/tojson-method-date-javascript.md)   
 [Aplicación de ejemplo de lector de fuentes (tienda Windows)](http://code.msdn.microsoft.com/Feed-reader-sample-99d68cf8)