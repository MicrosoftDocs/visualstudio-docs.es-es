---
title: String.fromCharCode (función de JavaScript) | Documentos de Microsoft
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
- fromCharCode
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- fromCharCodeAt method
- characters, from Unicode
ms.assetid: f64120c1-23a7-48ca-8d1c-db3e8856cab4
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dbcd9062d7da0b73647c1d9eb6cc207af23c3532
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639845"
---
# <a name="stringfromcharcode-function-javascript"></a>String.fromCharCode (Función de JavaScript)
Devuelve una cadena a partir de varios valores de caracteres Unicode.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
String.fromCharCode([code1[, code2[, ...[, codeN]]]])   
```  
  
## <a name="parameters"></a>Parámetros  
 `String`  
 Obligatorio. Objeto `String`.  
  
 `code1`, . . . , `codeN`  
 Opcional. Una serie de valores de caracteres Unicode para convertir en una cadena. Si no se proporcionan argumentos, el resultado es una cadena vacía.  
  
## <a name="remarks"></a>Comentarios  
 Llame a esta función en la `String` objeto en lugar de en una instancia de cadena.  
  
 En el ejemplo siguiente se muestra cómo utilizar este método:  
  
```JavaScript  
var test = String.fromCharCode(112, 108, 97, 105, 110);  
document.write(test);  
  
// Output: plain  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [charCodeAt (Método, String)](../../javascript/reference/charcodeat-method-string-javascript.md)