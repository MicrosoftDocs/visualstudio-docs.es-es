---
title: "replace (M&#233;todo, String de JavaScript) | Microsoft Docs"
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
  - "replace"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Replace (método)"
  - "reemplazar cadenas"
ms.assetid: 5f0e4765-df4d-4887-bd09-efe5e58251bf
caps.latest.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 28
---
# replace (M&#233;todo, String de JavaScript)
Reemplaza el texto de una cadena, usando una expresión regular o una cadena de búsqueda.  
  
## Sintaxis  
  
```  
  
stringObj. replace(rgExp, replaceText)  
```  
  
## Parámetros  
 `stringObj`  
 Obligatorio.  Objeto `String` o literal de cadena donde se realizará el reemplazo.  Esta cadena no se modifica con el método **replace**.  En su lugar, el valor devuelto de este método es la cadena generada por el reemplazo.  
  
 `rgExp`  
 Obligatorio.  Instancia de un objeto **Regular Expression** que contiene el patrón de expresión regular y las marcas aplicables.  También puede ser un objeto `String` o literal de cadena que representa la expresión regular.  Si `rgExp` no es una instancia de un objeto **Regular Expression**, se convierte en una cadena y se realiza una búsqueda exacta de resultados; en ningún momento se intentará convertir la cadena en una expresión regular.  
  
 `replaceText`  
 Obligatorio.  Objeto `String` o literal de cadena que contiene el texto que se va a reemplazar para cada coincidencia de `rgExp` en `stringObj`.  En [!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] o versiones posteriores, el argumento `replaceText` también puede ser una función que devuelve el texto de reemplazo.  
  
## Valor devuelto  
 El resultado del método **replace** es una copia de `stringObj` una vez realizados los reemplazos especificados.  
  
## Comentarios  
 Cualquiera de las siguientes variables de coincidencia pueden usarse para identificar la coincidencia más reciente y su cadena de procedencia.  Las variables de coincidencia pueden usarse para reemplazar texto cuando sea necesario determinar dinámicamente la cadena de reemplazo.  
  
|Caracteres|Significado|  
|----------------|-----------------|  
|**$$**|`$` \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] o versiones posteriores\)|  
|**$&**|Especifica la parte de `stringObj` que coincide con el patrón completo.  \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] o versiones posteriores\)|  
|`$``|Especifica la parte de `stringObj` que precede a la coincidencia descrita por **$&**.  \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] o versiones posteriores\)|  
|`$'`|Especifica la parte de `stringObj` que sigue a la coincidencia descrita por **$&**.  \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] o versiones posteriores\)|  
|`$`  ***n***|Subcoincidencia *n* capturada, donde *n* es un número decimal de un dígito comprendido entre 1 y 9.  \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] o versiones posteriores\)|  
|`$`  ***nn***|Subcoincidencia *nn* capturada, donde *nn* es un número decimal de dos dígitos comprendido entre 01 y 99.  \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] o versiones posteriores\)|  
  
 Si `replaceText` es una función, para cada subcadena encontrada se llama a la función con los siguientes argumentos *m* \+ 3, donde *m* es el número de paréntesis de captura de apertura de `rgExp`.  El primer argumento es la subcadena que coincide.  Los siguientes argumentos *m* son todas las capturas resultantes de la búsqueda.  El argumento *m* \+ 2 es el desplazamiento dentro de `stringObj` donde se produjo la coincidencia y el argumento *m* \+ 3 es `stringObj`.  El resultado es el valor de cadena que se obtiene al reemplazar cada subcadena coincidente por el valor devuelto correspondiente de la llamada de función.  
  
 El método **replace** actualiza las propiedades del objeto `RegExp` global.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método **replace** para reemplazar todas las instancias de "the" por "a".  
  
```javascript  
var s = "the batter hit the ball with the bat";  
  
// Replace "the" with "a".  
var re = /the/g;  
var result = s.replace(re, "a");  
document.write(result);  
// Output: a batter hit a ball with a bat  
```  
  
 Además, el método **replace** también puede reemplazar subexpresiones del patrón.  En el siguiente ejemplo, se intercambia cada par de palabras en la cadena.  
  
```javascript  
  
var s = "The quick brown fox jumped over the lazy dog.";  
var re = /(\S+)(\s+)(\S+)/g;  
// Exchange each pair of words.  
var result = s.replace(re, "$3$2$1");  
document.write(result);  
  
// Output:  quick The fox brown over jumps lazy the dog.  
```  
  
 En el ejemplo siguiente, que funciona en [!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] y versiones posteriores, se muestra cómo usar una función que devuelve el texto de reemplazo.  Reemplaza cualquier instancia de un número seguido de "F" con una conversión a Celsius.  
  
```javascript  
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
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [String \(Objeto\)](../../javascript/reference/string-object-javascript.md)  
  
## Vea también  
 [exec \(Método, Regular Expression\)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [match \(Método, String\)](../../javascript/reference/match-method-string-javascript.md)   
 [RegExp \(Objeto\)](../../javascript/reference/regexp-object-javascript.md)   
 [search \(Método, String\)](../../javascript/reference/search-method-string-javascript.md)   
 [test \(Método, Regular Expression\)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Regular Expression Programming \(JavaScript\)](http://msdn.microsoft.com/es-es/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [Alternation and Subexpressions \(JavaScript\)](http://msdn.microsoft.com/es-es/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [Backreferences \(JavaScript\)](http://msdn.microsoft.com/es-es/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)   
 [Aplicación de ejemplo de arrastrar y colocar de HTML5](http://code.msdn.microsoft.com/Drag-and-drop-e2701a72)