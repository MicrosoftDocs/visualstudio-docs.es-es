---
title: concat (método, String) (JavaScript) | Documentos de Microsoft
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
- concat
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- concat method (String)
- Concat method
ms.assetid: 5d28ebb2-d534-4179-9297-a4c821ee9f24
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b6419cc6404e06fc780802a30a3b4add8320881
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634005"
---
# <a name="concat-method-string-javascript"></a>concat (Método, String de JavaScript)
Devuelve una cadena que contiene la concatenación de dos o más cadenas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
string1. concat([string2[, string3[, . . . [, stringN]]]])  
```  
  
## <a name="parameters"></a>Parámetros  
 `string1`  
 Obligatorio. La `String` objeto o literal de cadena para que todos los demás especifica cadenas se concatenan.  
  
 `string2,. . ., stringN`  
 Opcional. Las cadenas que se anexará al final de `string1`.  
  
## <a name="remarks"></a>Comentarios  
 El resultado de la `concat` método es equivalente a: `result`  =  `string1`  +  `string2`  +  `string3`  +  `stringN`. Un cambio del valor de cadena de un origen o el resultado no afecta al valor en la otra cadena. Si alguno de los argumentos no son cadenas, primero se convierten en cadenas antes de concatenarse para `string1`.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la `concat` método cuando se utiliza con una cadena:  
  
```JavaScript  
var str1 = "ABCD"  
var str2 = "EFGH";  
var str3 = "1234";  
var str4 = "5678";  
document.write(str1.concat(str2, str3, str4));  
  
// Output: "ABCDEFGH12345678"  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [objeto de cadena](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [Operador de suma (+)](../../javascript/reference/addition-operator-decrement-javascript.md)