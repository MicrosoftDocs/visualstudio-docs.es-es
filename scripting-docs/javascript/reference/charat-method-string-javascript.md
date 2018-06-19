---
title: charAt (método, String) (JavaScript) | Documentos de Microsoft
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
- charAt
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- String object, returning characters
- charAt method
- characters, returning part of
ms.assetid: 63173e15-17f6-47c5-8f94-98ef1eb04c1a
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 201d85fec4ba184f0842c7401d986650b9ee078c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634135"
---
# <a name="charat-method-string-javascript"></a>charAt (Método, String de JavaScript)
Devuelve el carácter que se encuentra en el índice especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
strObj. charAt(index)  
```  
  
## <a name="parameters"></a>Parámetros  
 `strObj`  
 Obligatorio. Cualquier `String` objeto o literal de cadena.  
  
 `index`  
 Obligatorio. Índice de base cero del carácter deseado.  
  
## <a name="remarks"></a>Comentarios  
 El `charAt` método devuelve un valor de caracteres igual que el carácter en el índice especificado `index`. Es el primer carácter de una cadena en el índice 0, el segundo es en el índice 1 y así sucesivamente. Los valores de `index` que están fuera del intervalo de valor devuelto de una cadena vacía.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la `charAt` método:  
  
```JavaScript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";  
document.write(str.charAt(str.length - 1));  
  
// Output: Z  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [objeto de cadena](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [String (Objeto)](../../javascript/reference/string-object-javascript.md)