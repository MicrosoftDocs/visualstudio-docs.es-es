---
title: for... en (instrucción de JavaScript) | Documentos de Microsoft
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
- iteration statements, for...in statement
- loop structures, for...in statements
ms.assetid: 1b51a0ce-89f7-4a69-88ed-017b47dc398f
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a9c3ce78def6ab91256ff724a4acc87b7cf19ba2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636735"
---
# <a name="forin-statement-javascript"></a>for...in (Instrucción de JavaScript)
Ejecuta una o varias instrucciones para cada propiedad de un objeto o cada elemento de una matriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
for (variable in [object | array]) {  
    statements   
}  
```  
  
## <a name="parameters"></a>Parámetros  
 `variable`  
 Obligatorio. Una variable que puede ser cualquier nombre de propiedad de `object` o un índice de elemento de un `array`.  
  
 `object`, `array`  
 Opcional. Un objeto o matriz en la que se va a iterar.  
  
 `statements`  
 Opcional. Una o varias instrucciones que se ejecutarán para cada propiedad del `object` o cada elemento de `array`. Puede ser una instrucción compuesta.  
  
## <a name="remarks"></a>Comentarios  
 Al principio de cada iteración de un bucle, el valor de `variable` es el siguiente nombre de propiedad `object` o el índice del elemento siguiente del `array`. A continuación, puede usar `variable` en cualquiera de las instrucciones dentro del bucle para hacer referencia a la propiedad de `object` o el elemento de `array`.  
  
 No se asignan las propiedades de un objeto de una manera determinada. No se puede especificar una propiedad determinada por su índice únicamente mediante el nombre de la propiedad.  
  
 Recorrer en iteración una matriz se realiza en el orden de los elementos, es decir, 0, 1, 2.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la `for...in` instrucción con un objeto que se usa como una matriz asociativa.  
  
```JavaScript  
// Initialize object.  
a = {"a" : "Athens" , "b" : "Belgrade", "c" : "Cairo"}  
  
// Iterate over the properties.  
var s = ""  
for (var key in a) {  
    s += key + ": " + a[key];  
    s += "<br />";  
    }  
document.write (s);  
  
// Output:  
// a: Athens  
// b: Belgrade  
// c: Cairo  
```  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo muestra el uso de la `for ... in` instrucción para recorrer en iteración un `Array` objeto que tiene las propiedades expando.  
  
```JavaScript  
// Initialize the array.  
var arr = new Array("zero","one","two");  
  
// Add a few expando properties to the array.  
arr["orange"] = "fruit";  
arr["carrot"] = "vegetable";  
  
// Iterate over the properties and elements.  
var s = "";  
for (var key in arr) {  
    s += key + ": " + arr[key];  
    s += "<br />";  
}  
  
document.write (s);  
  
// Output:  
//   0: zero  
//   1: one  
//   2: two  
//   orange: fruit  
//   carrot: vegetable  
```  
  
> [!NOTE]
>  Use la `Enumerator` objeto para recorrer en iteración los miembros de una colección.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [para la instrucción](../../javascript/reference/for-statement-javascript.md)   
 [while (Instrucción)](../../javascript/reference/while-statement-javascript.md)