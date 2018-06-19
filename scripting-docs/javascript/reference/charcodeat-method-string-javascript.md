---
title: charCodeAt (método, String) (JavaScript) | Documentos de Microsoft
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
- charCodeAt
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- charCodeAt method
ms.assetid: 5b0290a7-ee4d-4738-a909-c02ef64a2f1a
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e7b8e62dfd29aa42d9816d0c5e27cc90440751a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633955"
---
# <a name="charcodeat-method-string-javascript"></a>charCodeAt (Método, String de JavaScript)
Devuelve el valor Unicode del carácter situado en la ubicación especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
strObj. charCodeAt(index)  
```  
  
## <a name="parameters"></a>Parámetros  
 `strObj`  
 Obligatorio. Cualquier `String` objeto o literal de cadena.  
  
 `index`  
 Obligatorio. Índice de base cero del carácter deseado. Si no hay ningún carácter en el índice especificado, `NaN` se devuelve.  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `charCodeAt`.  
  
```JavaScript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";   
document.write(str.charCodeAt(str.length - 1));  
  
// Output: 90   
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [String.fromCharCode (Función)](../../javascript/reference/string-fromcharcode-function-javascript.md)