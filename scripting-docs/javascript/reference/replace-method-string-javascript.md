---
title: Replace (método) (cadena) (JavaScript) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- replace
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- replacing strings
- Replace method
ms.assetid: 5f0e4765-df4d-4887-bd09-efe5e58251bf
caps.latest.revision: 28
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 82894a5d7f92c8231a6ba3a1948369fb2c819a6d
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2018
ms.locfileid: "27719349"
---
# <a name="replace-method-string-javascript"></a>replace (Método, String de JavaScript)
Reemplaza el texto de una cadena, usando una expresión regular o una cadena de búsqueda.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
stringObj.replace(rgExp, replaceText)  
```  
  
## <a name="parameters"></a>Parámetros  
 `stringObj`  
 Requerido. Objeto `String` o literal de cadena donde se realizará el reemplazo. Esta cadena no es modificada por la **reemplazar** método. En su lugar, el valor devuelto de este método es la cadena generada por el reemplazo.  
  
 `rgExp`  
 Requerido. Una instancia de un **expresión Regular** objeto que contiene el patrón de expresión regular y las marcas aplicables. También puede ser un objeto `String` o un literal de cadena que represente la expresión regular. Si `rgExp` no es una instancia de un **expresión Regular** objeto, se convierte en una cadena y se realizará una búsqueda exacta de los resultados; se realiza ningún intento para convertir la cadena en una expresión regular.  
  
 `replaceText`  
 Requerido. Objeto `String` o literal de cadena que contiene el texto para reemplazar en cada coincidencia correcta de `rgExp` en `stringObj`. En [!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] o versiones posteriores, el argumento `replaceText` también puede ser una función que devuelve el texto de reemplazo.  
  
## <a name="return-value"></a>Valor devuelto  
 El resultado de la **reemplazar** método es una copia de `stringObj` una vez realizados los reemplazos especificados.  
  
## <a name="remarks"></a>Comentarios  
 Se puede utilizar cualquiera de las siguientes variables de coincidencia para identificar la coincidencia más reciente y la cadena de procedencia. Las variables de coincidencia se pueden utilizar en texto de reemplazo cuando la cadena de reemplazo se tenga que determinar dinámicamente.  
  
|Caracteres|Significado|  
|----------------|-------------|  
|**$$**|`$` ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] o posterior)|  
|**$&**|Especifica la parte de `stringObj` que coincide con el patrón completo. ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] o posterior)|  
|`$``|Especifica la parte de `stringObj` que precede a la coincidencia descrita por  **$&** . ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] o posterior)|  
|`$'`|Especifica la parte de `stringObj` que sigue a la coincidencia descrita por  **$&** . ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] o posterior)|  
|`$`  ***n***|El  *n* Subcoincidencia n, donde  *n*  es un único dígito decimal comprendido entre 1 y 9. ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] o posterior)|  
|`$`  ***nn***|El  *nn* Subcoincidencia n, donde  *nn*  es un número decimal de dos dígitos entre 01 y 99. ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] o posterior)|  
  
 Si `replaceText` es una función, para cada subcadena encontrada la función se denomina con el siguiente *m* + 3 argumentos donde *m* es el número de paréntesis de captura que queden el `rgExp`. El primer argumento es la subcadena que ha coincidido. La siguiente *m* argumentos son todas las capturas resultantes de la búsqueda. Argumento *m* + 2 es el desplazamiento dentro de `stringObj` donde se produjo la coincidencia y el argumento *m* + 3 es `stringObj`. El resultado es el valor de cadena que se obtiene al reemplazar cada coincidencia de la subcadena por el correspondiente valor devuelto por la llamada a la función.  
  
 El **reemplazar** método actualiza las propiedades de la información global `RegExp` objeto.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la **reemplazar** método para reemplazar todas las instancias de "the" por "a".  
  
```JavaScript  
var s = "the batter hit the ball with the bat";  
  
// Replace "the" with "a".  
var re = /the/g;  
var result = s.replace(re, "a");  
document.write(result);  
// Output: a batter hit a ball with a bat  
```  
  
 Además, el **reemplazar** método también puede reemplazar subexpresiones en el modelo. En el siguiente ejemplo, se intercambia cada par de palabras en la cadena.  
  
```JavaScript  
  
var s = "The quick brown fox jumped over the lazy dog.";  
var re = /(\S+)(\s+)(\S+)/g;  
// Exchange each pair of words.  
var result = s.replace(re, "$3$2$1");  
document.write(result);  
  
// Output:  quick The fox brown over jumped lazy the dog.  
```  
  
 En el ejemplo siguiente, que funciona en [!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] y versiones posteriores, se muestra cómo usar una función que devuelve el texto de reemplazo. Reemplaza cualquier instancia de un número seguido de “F” con una conversión a Celsius.  
  
```JavaScript  
function f2c(s1) {  
    // Initialize pattern.  
    var test = /(\d+(\.\d*)?)F\b/g;  
  
    // Use a function for the replacement.  
    var s2 = s1.replace(test,  
      function($0,$1,$2)  
           {   
           return((($1-32) * 5/9) + "C");  
           }  
        )  
    return s2;  
}  
document.write(f2c("Water freezes at 32F and boils at 212F."));  
  
// Output: Water freezes at 0C and boils at 100C.  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [objeto de cadena](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [exec (método, Regular Expression)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [Match (método) (cadena)](../../javascript/reference/match-method-string-javascript.md)   
 [RegExp (objeto)](../../javascript/reference/regexp-object-javascript.md)   
 [Buscar (método, String)](../../javascript/reference/search-method-string-javascript.md)   
 [Test (método) (expresión Regular)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Programación de la expresión regular (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [Alternancia y subexpresiones (JavaScript)](http://msdn.microsoft.com/en-us/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [Referencias inversas (JavaScript)](http://msdn.microsoft.com/en-us/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)   
 [HTML5 arrastrar y colocar la aplicación de ejemplo](http://code.msdn.microsoft.com/Drag-and-drop-e2701a72)