---
title: decodeURI (función) (JavaScript) | Documentos de Microsoft
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
- decodeURI
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- decodeURI method
ms.assetid: af6c81dc-10f4-4243-a7ce-d18ae3ea0fb8
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 97291142083ae88c7dc84d9cd08af5c3c39ff9e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636245"
---
# <a name="decodeuri-function-javascript"></a>decodeURI (Función de JavaScript)
Obtiene la versión sin codificar de un identificador uniforme de recursos (URI) codificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
decodeURI(URIstring)  
```  
  
## <a name="remarks"></a>Comentarios  
 Requerido `URIstring` argumento es un valor que representa un identificador URI codificado.  
  
 Use la `decodeURI` función en lugar de las regiones `unescape` función.  
  
 El `decodeURI` función devuelve un valor de cadena.  
  
 Si el `URIString` no es válido, se produce un Error URIError.  
  
 **Se aplica a**: [Global (objeto)](../../javascript/reference/global-object-javascript.md)  
  
## <a name="example"></a>Ejemplo  
 El código siguiente primero codifica un componente URI y luego los descodifica.  
  
```JavaScript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write ("<br/>");  
document.write (uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [decodeURIComponent (función)](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [encodeURI (función)](../../javascript/reference/encodeuri-function-javascript.md)   
 [Objeto Global](../../javascript/reference/global-object-javascript.md)