---
title: "encodeURIComponent (función) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: encodeURIComponent
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: encodeURIComponent method
ms.assetid: 8202bce6-1342-40dc-a5ef-ac6d210a7d15
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56680e9bcfe1de61d8a1eabd0ff8d2eced01d603
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="encodeuricomponent-function-javascript"></a>encodeURIComponent (Función de JavaScript)
Codifica una cadena de texto como un componente válido de un identificador uniforme de recursos (URI).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
encodeURIComponent(encodedURIString)  
```  
  
## <a name="remarks"></a>Comentarios  
 Requerido `encodedURIString` argumento es un valor que representa un componente de URI codificado.  
  
 El `encodeURIComponent` función devuelve un identificador URI codificado. Si se pasa el resultado a `decodeURIComponent`, se devuelve la cadena original. Dado que la `encodeURIComponent` función codifica todos los caracteres, debe tener cuidado si la cadena representa una ruta de acceso como **/folder1/folder2/default.html**. Los caracteres de barra diagonal se codificarán y no serán válidos si se envían como una solicitud a un servidor web. Use la `encodeURI` funcionar si la cadena contiene más de un componente de URI único.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente primero codifica un componente URI y luego los descodifica.  
  
```JavaScript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [decodeURI (función)](../../javascript/reference/decodeuri-function-javascript.md)   
 [DecodeURIComponent (Función)](../../javascript/reference/decodeuricomponent-function-javascript.md)