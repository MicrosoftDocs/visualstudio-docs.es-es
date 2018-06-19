---
title: encodeURI (función) (JavaScript) | Documentos de Microsoft
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
- encodeURI
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- encodeURI method
ms.assetid: 17bab5a2-bcd4-46c2-8b52-b2b5a0ed98a3
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8cf9bbdf34c0481c889d1176bc32ab0246a333a4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636425"
---
# <a name="encodeuri-function-javascript"></a>encodeURI (Función de JavaScript)
Codifica una cadena de texto como un identificador uniforme de recursos (URI) válido  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
encodeURI(  
URIString  
)  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Requerido `URIString` argumento es un valor que representa un identificador URI codificado.  
  
 El `encodeURI` función devuelve un identificador URI codificado. Si se pasa el resultado a `decodeURI`, se devuelve la cadena original. El `encodeURI` función no codifica los siguientes caracteres: ":", "/", ";" y "?". Use `encodeURIComponent` para codificar estos caracteres.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente se codifica en primer lugar y, a continuación, descodifica un URI.  
  
```JavaScript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [decodeURI (función)](../../javascript/reference/decodeuri-function-javascript.md)   
 [DecodeURIComponent (Función)](../../javascript/reference/decodeuricomponent-function-javascript.md)