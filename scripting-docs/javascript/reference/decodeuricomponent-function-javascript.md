---
title: "decodeURIComponent (función) (JavaScript) | Documentos de Microsoft"
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
- decodeURIComponent
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- decodeURIComponent method
ms.assetid: 486ccee2-afd7-4863-97ce-4adb50cf39c0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef7bdcd374a328bad632381d19e9823853d37f01
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="decodeuricomponent-function-javascript"></a>decodeURIComponent (Función de JavaScript)
Obtiene la versión sin codificar de un componente codificado de un identificador uniforme de recursos (URI).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
decodeURIComponent(encodedURIString)  
```  
  
## <a name="remarks"></a>Comentarios  
 Requerido `encodedURIString` argumento es un valor que representa un componente de URI codificado.  
  
 Un componente de URI forma parte de un URI completo.  
  
 Si el `encodedURIString` no es válido, se produce un Error URIError.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente se codifica en primer lugar y, a continuación, descodifica un URI.  
  
```JavaScript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write("<br/>");  
document.write (uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [decodeURI (función)](../../javascript/reference/decodeuri-function-javascript.md)   
 [encodeURI (Función)](../../javascript/reference/encodeuri-function-javascript.md)