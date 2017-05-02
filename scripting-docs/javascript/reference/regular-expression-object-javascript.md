---
title: "Regular Expression (Objeto de JavaScript) | Microsoft Docs"
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
  - "RegularExpression_JavaScript"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "RegExp (objeto), información general"
  - "Regular Expression (objeto)"
  - "expresiones regulares, RegExp (objeto)"
ms.assetid: 346aa83e-a045-47ea-acae-b42c7b121534
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# Regular Expression (Objeto de JavaScript)
Un objeto que contiene un patrón de expresión regular junto con marcas que identifican cómo aplicar dicho patrón.  
  
## Sintaxis  
  
```  
re = /pattern/[flags]  
```  
  
## Sintaxis  
  
```  
re = new RegExp("pattern"[,"flags"])   
```  
  
## Parámetros  
 *re*  
 Requerido.  El nombre de variable al que se asigna el patrón de expresión regular.  
  
 *pattern*  
 Requerido.  El patrón de expresión regular a utilizar.  Si utiliza la sintaxis 1, delimite el modelo con caracteres "\/".  Si utiliza la sintaxis 2, delimite el patrón con comillas.  
  
 `flags`  
 Opcional.  Si utiliza la sintaxis 2, delimite la marca entre comillas.  Los marcadores disponibles, que se pueden combinar, son:  
  
-   g \(búsqueda global para todas las apariciones del *patrón*\)  
  
-   i \(no distinguir mayús.\/minús.\)  
  
-   m \(búsqueda de múltiples líneas\)  
  
-   u \(unicode\), habilita las [características Unicode](../../javascript/advanced/special-characters-javascript.md) EcmaScript 6.  Solo se admite en [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)].  
  
-   y \(coincidencia rápida\), busca coincidencias en la propiedad `lastIndex` de la expresión regular \(y no busca en los índices posteriores\).  Se admite en [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)].  
  
## Comentarios  
 El objeto **Expresión regular** no debe confundirse con el objeto `RegExp` global.  Aunque parecen el mismo, son independientes y distintos.  Las propiedades del objeto **Expresión regular** contienen solo información sobre una determinada instancia de **Expresión regular**, mientras que las propiedades del objeto `RegExp` global contienen información continuamente actualizada sobre cada coincidencia que tiene lugar.  
  
 Los objetos **Expresión regular** almacenan patrones utilizados al buscar cadenas para combinaciones de caracteres.  Tras su creación, el objeto **Expresión regular** se pasa a un método de cadena, o bien se pasa una cadena a uno de los métodos de expresión regular.  La información sobre la última búsqueda realizada se guarda en el objeto `RegExp` global.  
  
 Utilice la sintaxis 1 cuando ya conozca la cadena de búsqueda.  Utilice la sintaxis 2 cuando la cadena de búsqueda cambie con frecuencia o se desconozca, por ejemplo, cuando son cadenas proporcionadas por el usuario.  
  
 El argumento *patrón* se compila en un formato interno antes de su uso.  En la sintaxis 1, *patrón* se compila cuando se carga el script.  En la sintaxis 2, *patrón* se compila justo antes de su uso, o cuando se llama al método **compilar**.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del objeto **Expresión regular** mediante la creación de un objeto \(re\) que contiene un patrón de expresión regular con sus marcas asociadas.  En este caso, el objeto **Expresión regular** resultante lo usa después el método `match`:  
  
```javascript  
var s = "through the pages of the book";  
  
// Create regular expression pattern.  
var re = new RegExp("the", "i");  
  
// Attempt match on search string.  
var r = s.match(re);     
  
// Return first occurrence of "the".  
if(console && console.log) {  
    console.log(r);  
}  
  
// Output:  
//   
```  
  
## Ejemplo  
 En el ejemplo siguiente se actualiza el patrón de expresión regular para buscar varias instancias.  
  
```javascript  
// Create regular expression pattern using the i and g flags.  
var re = new RegExp("the", "ig");  
  
// Attempt match on search string.  
var r = s.match(re);     
  
// Return the two occurrences of "the".  
if(console && console.log) {  
    console.log(r.length);  
    console.log(r);  
}  
  
// Output:  
// 2  
// [object Array] ["the", "the"]  
```  
  
## Ejemplo  
 Cuando se usa el marcador \/y, si se produce una coincidencia se actualiza el `lastindex` al índice del carácter siguiente después de la última coincidencia.  En caso de no haber coincidencia, el `lastindex` se establece en 0.  
  
 En el ejemplo siguiente se busca una coincidencia en un índice específico mediante la marca \/y y la propiedad `lastIndex`.  
  
```javascript  
// Create regular expression pattern using the i and y flags.  
var re = new RegExp("the", "iy");  
  
// Set the lastIndex property and attempt a match  
// at the specified index.  
re.lastIndex = 20;  
var r = s.match(re);     
  
// No matches returned.  
if(console && console.log) {  
    console.log(r);  
}  
// Reset the lastIndex property and attempt a match.  
re.lastIndex = 21;  
var r = s.match(re);  
  
// Return occurrence of "the" starting at index 21.  
if(console && console.log) {  
    console.log(r);  
}  
  
// Output:  
// null  
// [object Array] ["the"]  
```  
  
<a name="js56jsobjregexpressionprop"></a>   
## Propiedades  
 [global \(Propiedad\)](../../javascript/reference/global-property-regular-expression-javascript.md) &#124; [ignoreCase \(Propiedad\)](../../javascript/reference/ignorecase-property-regular-expression-javascript.md) &#124; [multiline \(Propiedad\)](../../javascript/reference/multiline-property-regular-expression-javascript.md) &#124; [source \(Propiedad\)](../../javascript/reference/source-property-regular-expression-javascript.md)  
  
<a name="js56jsobjregexpressionmeth"></a>   
## Métodos  
 [compile \(Método\)](../../javascript/reference/compile-method-regular-expression-javascript.md) &#124; [exec \(Método\)](../../javascript/reference/exec-method-regular-expression-javascript.md) &#124; [test \(Método\)](../../javascript/reference/test-method-regular-expression-javascript.md)  
  
## Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 La marca u se admite en [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)].  
  
 La marca y se admite en [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)].  
  
## Vea también  
 [RegExp \(Objeto\)](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/es-es/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [String \(Objeto\)](../../javascript/reference/string-object-javascript.md)