---
title: "unescape (función) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: unescape
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Unescape method
ms.assetid: 4adf0270-88b5-4d54-8110-d879d6ae97c2
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 96601fc21f47c86aec8c3702a6861c3676aacacf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="unescape-function-javascript"></a>unescape (Función de JavaScript)
Descodifica `String` codifican los objetos con el `escape` función. Desusado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
unescape(charString)   
```  
  
## <a name="remarks"></a>Comentarios  
 Requerido `charString` argumento es un `String` literal u objeto que se desea descodificar.  
  
 El `unescape` función devuelve un valor de cadena que contiene el contenido de `charstring`. Todos los caracteres codificados con el %*xx* formato hexadecimal se reemplazan por sus equivalentes del juego de caracteres ASCII.  
  
 Los caracteres codificados en **%u** *xxxx* formato (caracteres Unicode) se reemplazan con el carácter Unicode con codificación hexadecimal *xxxx*.  
  
> [!NOTE]
>  El `unescape` función no debe utilizarse para descodificar identificadores de recursos uniformes (URI). Use `decodeURI` y `decodeURIComponent` funciona en su lugar.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Global (objeto)](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [decodeURI (función)](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent (función)](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [escape (función)](../../javascript/reference/escape-function-javascript.md)   
 [String (Objeto)](../../javascript/reference/string-object-javascript.md)