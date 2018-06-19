---
title: Compare (propiedad, Intl.Collator) | Documentos de Microsoft
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
ms.assetid: 59f274dc-6e52-4344-8d5c-b9f0000b66e0
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5bfd222ac8d2c94efe279177e7f4d8ffdf850f44
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634175"
---
# <a name="compare-property-intlcollator"></a>compare (Propiedad, Intl.Collator)
Devuelve una función que compara dos cadenas mediante el criterio de ordenación del clasificador.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
collatorObj.compare  
```  
  
#### <a name="parameters"></a>Parámetros  
 `collatorObj`  
 Obligatorio. El nombre de la `Collator` objeto que se va a utilizar para la comparación.  
  
## <a name="remarks"></a>Comentarios  
 La función devuelta por la `compare` propiedad toma dos argumentos, `x` y `y`y devuelve el resultado de una comparación de la configuración regional de `x` y `y` mediante el uso de las opciones especificadas en el `Collator` objeto.  
  
 Puede ser el resultado de la comparación:  
  
-   -1 si `x` antes `y` en el criterio de ordenación.  
  
-   0 (cero) si `x` es igual a `y` en el criterio de ordenación.  
  
-   1 si `x` después `y` en el criterio de ordenación.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se crea un `Collator` de objeto y realiza una comparación.  
  
```JavaScript  
var co = new Intl.Collator(["de-DE-u-co-phonebk"]);  
  
if (console && console.log) {  
    console.log(co.compare("a", "b")); // Returns -1  
}  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se utiliza `Collator` objetos que se va a ordenar una matriz. Este ejemplo muestra las diferencias de configuración regional.  
  
```JavaScript  
var co1 = new Intl.Collator(["de-DE-u-co-phonebk"]);  
var co2 = new Intl.Collator(["de-DE"]);  
var co3 = new Intl.Collator(["en-US"]);  
  
var arr = ["ä", "ad", "af", "a"];  
  
if (console && console.log) {  
    console.log(arr.sort(co1.compare));  // Returns a,ad,ä,af  
    console.log(arr.sort(co2.compare));  // Returns a,ä,ad,af  
    console.log(arr.sort(co3.compare));  // Returns a,ä,ad,af  
}  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se usa un `Collator` objeto que se va a buscar una cadena.  
  
```JavaScript  
// String to search  
var arr = ["ä", "ad", "af", "a"];  
// String searched for  
var s = "af";  
  
var co = new Intl.Collator("de-DE", { usage: "search" });  
var matches = arr.filter(function (i) {  
    return co.compare(i, s) === 0;  
});  
  
if (console && console.log) {  
    console.log(matches);  // Returns af  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Intl.Collator (Objeto)](../../javascript/reference/intl-collator-object-javascript.md)