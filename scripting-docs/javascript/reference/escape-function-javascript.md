---
title: escape (función) (JavaScript) | Documentos de Microsoft
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
- escape
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- encoding string objects
- Escape method
- hexadecimal
- String object, encoding
ms.assetid: caa92bea-ba69-4109-a68a-6e2debda463a
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b53a447ae6dde917c12a4711d9038136dc4500cf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636515"
---
# <a name="escape-function-javascript"></a>escape (Función de JavaScript)
Codifica las cadenas para que se puedan leer en todos los equipos. Desusado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
escape(charString)   
```  
  
## <a name="remarks"></a>Comentarios  
 Requerido `charString` argumento es cualquier `String` literal u objeto que codificarse.  
  
 El **escape** función devuelve un valor de cadena (en formato Unicode) que contiene el contenido de `charstring`. Todos los espacios, signos de puntuación, acentuadas caracteres y cualquier otro carácter no ASCII se reemplaza con `%` *xx* codificación, donde *xx* equivale a la número hexadecimal que representa el carácter. Por ejemplo, un espacio se devuelve como "% 20".  
  
 Caracteres con un valor mayor que 255 se almacenan mediante el **%u** *xxxx* formato.  
  
> [!NOTE]
>  El **escape** función no debe usarse para codificar los identificadores uniformes de recursos (URI). Use `encodeURI` y `encodeURIComponent` funciona en su lugar.  
  
 **Se aplica a**: [Global (objeto)](../../javascript/reference/global-object-javascript.md)  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [encodeURI (función)](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent (función)](../../javascript/reference/encodeuricomponent-function-javascript.md)   
 [String (objeto)](../../javascript/reference/string-object-javascript.md)   
 [unescape (Función)](../../javascript/reference/unescape-function-javascript.md)