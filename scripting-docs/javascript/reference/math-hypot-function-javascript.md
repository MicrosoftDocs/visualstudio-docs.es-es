---
title: Función Math.hypot (JavaScript) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 31488f5a-2230-4114-911e-b6d854c7b0a0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a66c0b082356b8dde3f51f739c130378d694f3b4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638265"
---
# <a name="mathhypot-function-javascript"></a>Función Math.hypot (JavaScript)
Devuelve la raíz cuadrada de la suma de los cuadrados de los argumentos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Math.hypot ( value1[, value2[, ...values] );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `value1`  
 Obligatorio. Primer número.  
  
 `value2`  
 Opcional. Segundo número.  
  
 `values`  
 Opcional. Uno o varios números.  
  
## <a name="remarks"></a>Comentarios  
 Si algún argumento es NaN, la función devuelve NaN. Si no se proporciona ningún argumento, la función devuelve 0.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un ejemplo del uso de la función `Math.hypot`.  
  
```JavaScript  
Math.hypot(3, 4);  
// Returns 5  
  
Math.hypot(3, "4");  
// Returns 5  
  
Math.hypot(3, "four");  
// Returns NaN   
  
Math.hypot(3, 4, 10);  
// Returns 11.180339887498949  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]