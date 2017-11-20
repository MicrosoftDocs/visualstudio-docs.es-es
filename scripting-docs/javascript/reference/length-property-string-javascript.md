---
title: Length (propiedad, String) (JavaScript) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strings [Visual Studio], length
- Length property
- length property (String)
ms.assetid: 7dbd4a0e-c24e-4561-9b5b-e75e649a10a4
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 706a7f6986086f95613e09b9a8355eb5bc2702a7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="length-property-string-javascript"></a>length (Propiedad, String de JavaScript)
Devuelve la longitud de un objeto `String`.  
  
> [!WARNING]
>  Las cadenas de JavaScript son inmutables, por lo que no se puede modificar la longitud de una cadena.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      strVariable.length  
"String Literal".length   
```  
  
## <a name="remarks"></a>Comentarios  
 El `length` propiedad contiene un entero que indica el número de caracteres en la `String` objeto. El último carácter de la `String` objeto tiene un índice de`length` - 1.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente código se muestra cómo usar `length`: Cadenas de JavaScript son inmutables y no se puede modificar en su lugar. Sin embargo, puede escribir la cadena invertida en una matriz y, a continuación, llamar a `join` con el carácter vacío, lo que genera una cadena con ningún carácter separador.  
  
```JavaScript  
var str = "every good boy does fine";  
        var start = 0;  
        var end = str.length - 1;  
        var tmp = "";  
        var arr = new Array(end);  
  
        while (end >= 0) {  
            arr[start++] = str.charAt(end--);  
        }  
  
// Join the elements of the array with a   
        var str2 = arr.join('');  
        document.write(str2);  
  
// Output: enif seod yob doog yreve  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]