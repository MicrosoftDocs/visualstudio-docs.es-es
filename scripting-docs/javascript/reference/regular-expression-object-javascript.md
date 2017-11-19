---
title: "Objeto de expresión regular (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: RegularExpression_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Regular Expression object
- regular expressions, RegExp object
- RegExp object, overview
ms.assetid: 346aa83e-a045-47ea-acae-b42c7b121534
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df2d07e3b47e315ec804e5a7f20024dc2184eef0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="regular-expression-object-javascript"></a>Regular Expression (Objeto de JavaScript)
Un objeto que contiene un patrón de expresión regular junto con marcas que identifican cómo aplicar dicho patrón.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
re = /pattern/[flags]  
```  
  
## <a name="syntax"></a>Sintaxis  
  
```  
re = new RegExp("pattern"[,"flags"])   
```  
  
## <a name="parameters"></a>Parámetros  
 *Re*  
 Obligatorio. El nombre de variable al que se asigna el patrón de expresión regular.  
  
 *patrón*  
 Obligatorio. El patrón de expresión regular a utilizar. Si utiliza la sintaxis 1, delimite el modelo con caracteres "/". Si utiliza la sintaxis 2, delimite el patrón con comillas.  
  
 `flags`  
 Opcional. Si utiliza la sintaxis 2, delimite la marca entre comillas. Los marcadores disponibles, que se pueden combinar, son:  
  
-   g (búsqueda global para todas las apariciones de *patrón*)  
  
-   i (no distinguir mayús./minús.)  
  
-   m (búsqueda de múltiples líneas)  
  
-   u (unicode), habilita EcmaScript 6 [características Unicode](../../javascript/advanced/special-characters-javascript.md). Solo se admite en [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)].  
  
-   y (coincidencia rápida), busca coincidencias en la propiedad `lastIndex` de la expresión regular (y no busca en los índices posteriores). Se admite en [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)].  
  
## <a name="remarks"></a>Comentarios  
 El **expresión Regular** objeto no debe confundirse con la información global `RegExp` objeto. Aunque parecen el mismo, son independientes y distintos. Las propiedades de la **expresión Regular** objeto solo contienen información sobre una determinada **expresión Regular** instancia, mientras que las propiedades de la información global `RegExp` contienen el objeto continuamente información actualizada sobre cada coincidencia que tiene lugar.  
  
 **Expresión regular** objetos almacenan patrones utilizados al buscar cadenas para combinaciones de caracteres. Después de la **expresión Regular** se crea el objeto, se pasa a un método de cadena o se pasa una cadena a uno de los métodos de expresión regular. La información sobre la última búsqueda realizada se guarda en el objeto `RegExp` global.  
  
 Utilice la sintaxis 1 cuando ya conozca la cadena de búsqueda. Utilice la sintaxis 2 cuando la cadena de búsqueda cambie con frecuencia o se desconozca, por ejemplo, cuando son cadenas proporcionadas por el usuario.  
  
 El *patrón* argumento se compila en un formato interno antes de su uso. En la sintaxis 1, *patrón* se compila cuando se carga el script. En la sintaxis 2, *patrón* se compila justo antes de su uso, o cuando la **compilar** se llama al método.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la **expresión Regular** objeto mediante la creación de un objeto (re) que contiene un patrón de expresión regular con sus marcas asociadas. En este caso, el cuadro **expresión Regular** , a continuación, se utiliza el objeto por el `match` método:  
  
```JavaScript  
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
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se actualiza el patrón de expresión regular para buscar varias instancias.  
  
```JavaScript  
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
  
## <a name="example"></a>Ejemplo  
 Cuando se usa el marcador /y, si se produce una coincidencia se actualiza el `lastindex` al índice del carácter siguiente después de la última coincidencia. En caso de no haber coincidencia, el `lastindex` se establece en 0.  
  
 En el ejemplo siguiente se busca una coincidencia en un índice específico mediante la marca /y y la propiedad `lastIndex`.  
  
```JavaScript  
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
## <a name="properties"></a>Propiedades  
 [Propiedad global](../../javascript/reference/global-property-regular-expression-javascript.md) &#124; [ignoreCase (propiedad)](../../javascript/reference/ignorecase-property-regular-expression-javascript.md) &#124; [multiline (propiedad)](../../javascript/reference/multiline-property-regular-expression-javascript.md) &#124; [source (propiedad)](../../javascript/reference/source-property-regular-expression-javascript.md)  
  
<a name="js56jsobjregexpressionmeth"></a>   
## <a name="methods"></a>Métodos  
 [Compile (método)](../../javascript/reference/compile-method-regular-expression-javascript.md) &#124; [exec (método)](../../javascript/reference/exec-method-regular-expression-javascript.md) &#124; [test (método)](../../javascript/reference/test-method-regular-expression-javascript.md)  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 La marca u se admite en [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)].  
  
 La marca y se admite en [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)].  
  
## <a name="see-also"></a>Vea también  
 [RegExp (objeto)](../../javascript/reference/regexp-object-javascript.md)   
 [Sintaxis de expresión regular (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [String (Objeto)](../../javascript/reference/string-object-javascript.md)