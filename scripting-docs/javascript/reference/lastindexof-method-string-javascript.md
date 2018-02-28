---
title: "lastIndexOf (método, String) (JavaScript) | Documentos de Microsoft"
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
- lastIndexOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- lastIndexOf method, string
- string, lastIndexOf method
ms.assetid: 1ed36ccd-0f0b-4f16-be45-0567207670af
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0fa0f35e970435a4d0296493c20afdeaac128cae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="lastindexof-method-string-javascript"></a>lastIndexOf (Método, String de JavaScript)
Devuelve la última aparición de una subcadena de la cadena.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
strObj.lastIndexOf(substring[, startindex])  
```  
  
## <a name="parameters"></a>Parámetros  
 `strObj`  
 Obligatorio. Objeto `String` o literal de cadena.  
  
 `substring`  
 Obligatorio. La subcadena que se va a buscar.  
  
 `startindex`  
 Opcional. Índice en el que se va a comenzar la búsqueda. Si se omite, la búsqueda comienza al final de la cadena.  
  
## <a name="remarks"></a>Comentarios  
 El **lastIndexOf** método devuelve un valor entero que indica el principio de la subcadena dentro de la `String` objeto. Si no se encuentra la subcadena, se devuelve -1.  
  
 Si `startindex` es negativo, `startindex` se trata como cero. Si es mayor que el mayor índice de posición de carácter, se trata como el índice más grande posible.  
  
 La búsqueda se realiza empezando por el último carácter de la cadena. En caso contrario, este método es idéntico a **indexOf**.  
  
 En el ejemplo siguiente se muestra el uso de la **lastIndexOf** método.  
  
```JavaScript  
var str = "time, time";  
  
var s = "";  
s += "time is at position " + str.lastIndexOf("time");  
s += "<br />";  
s += "abc is at position " + str.lastIndexOf("abc");  
  
document.write(s);  
  
// Output:  
// time is at position 6  
// abc is at position -1  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [objeto de cadena](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [indexOf (Método, String)](../../javascript/reference/indexof-method-string-javascript.md)