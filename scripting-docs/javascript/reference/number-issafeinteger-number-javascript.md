---
title: "Number.isSafeInteger (número) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: c7ef6ce8-fe71-4e53-be44-4dd440aef21d
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eebc2147bc5043341be7e883548af825922036f9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="numberissafeinteger-number-javascript"></a>Number.isSafeInteger (número) (JavaScript)
Devuelve un valor booleano que indica si un número puede representarse de forma segura en JavaScript.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Number.isSafeInteger(numValue)   
```  
  
## <a name="return-value"></a>Valor devuelto  
 `true` si el número está entre `Number.MIN_SAFE_INTEGER` y `Number.MAX_SAFE_INTEGER`, ambos incluidos; en caso contrario, `false`.  
  
## <a name="remarks"></a>Comentarios  
 Un entero seguro en JavaScript es un número de precisión doble IEEE-754 antes de que se aplique redondeo.  
  
## <a name="example"></a>Ejemplo  
  
```JavaScript  
// Returns true  
Number.isSafeInteger(-100)  
Number.isSafeInteger(9007199254740991)  
  
// Returns false  
Number.isSafeInteger(Number.NaN)  
Number.isSafeInteger(Infinity)  
Number.isSafeInteger("100")  
Number.isSafeInteger(9007199254740992);  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Se aplica a**: [número de objeto](../../javascript/reference/number-object-javascript.md)