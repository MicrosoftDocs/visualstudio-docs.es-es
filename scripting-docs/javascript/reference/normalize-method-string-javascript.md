---
title: "Método Normalize (String) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d50077c1-b5fa-4e7a-9c9d-dc66cfc423ac
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aece38339ea1ce8924f404938b2d35d07504d539
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="normalize-method-string-javascript"></a>Método normalize (String) (JavaScript)
Devuelve la forma de normalización Unicode de una cadena especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
stringObj.normalize([form]);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `stringObj`  
 Obligatorio. El objeto de cadena con el que se contrasta.  
  
 `form`  
 Opcional. El valor de forma de normalización Unicode.  
  
## <a name="return-value"></a>Valor devuelto  
 La forma de normalización Unicode de una cadena especificada.  
  
## <a name="exceptions"></a>Excepciones  
 Si `form` es un valor no admitido, se produce un `RangeError`.  
  
## <a name="remarks"></a>Comentarios  
 Si `stringObj` no es una cadena, se convertirá en una cadena antes de que el método intente devolver la forma de normalización Unicode de la cadena.  
  
 `form`debe ser un valor de la forma de normalización Unicode, "NFC", "NFD", "NFKC" o "NFKD", correspondiente a los valores especificados para [Unicode estándar anexo #15](http://www.unicode.org/reports/tr15/). El valor predeterminado de `form` es “NFC”.  
  
## <a name="example"></a>Ejemplo  
 En los siguientes ejemplos de código se muestra el uso del método `normalize`.  
  
```JavaScript  
// ANGSTORM SIGN and LATIN CAPITAL A WITH RING ABOVE is canonically equivalent  
"\u212b".normalize("NFC") === "\u00c5";  
  
// Decomposed, ANGSTOM SIGN is LATIN CAPITAL A followed by COMBINING RING ABOVE  
"\u212b".normalize("NFD") === "\u0041\u030a"  
  
// Normalization Form C will combine the result back into the precombined character  
"\u0041\u030a".normalize("NFC") === "\u00c5"  
  
// LATIN SMALL LIGATURE FI is compatibility equivalent with LATIN SMALL LETTER F followed by  
// LATIN SMALL LETTER I.  
"\ufb01".normalize("NFKD") === "fi";  
  
// Same mapping in NFKC  
"\ufb01".normalize("NFKC") === "fi";  
  
// NFKC will not recombine compatibility characters.  
"fi".normalize("NFKC") === "fi";  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]