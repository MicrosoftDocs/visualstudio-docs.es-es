---
title: "Función Math.imul (JavaScript) | Documentos de Microsoft"
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
ms.assetid: dce5e11c-36b9-4c39-84d3-6cd494dd1cbf
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57820d0926d574c75924f4eef6265ef7fa0766da
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="mathimul-function-javascript"></a>Función Math.imul (JavaScript)
Devuelve el producto de dos números que se tratan como enteros de 32 bits con signo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Math.imul(x, y);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `x`  
 Obligatorio. Primer número.  
  
 `y`  
 Obligatorio. Segundo número.  
  
## <a name="remarks"></a>Comentarios  
 Esta función se usa para los compiladores como Emscripten y Mandreel, que no implementan la multiplicación de enteros de la misma manera que JavaScript.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo multiplicar números con `Math.imul`.  
  
```JavaScript  
var result1 = Math.imul(2, 5);  
// result1 == 10  
  
var result2 = Math.imul(Math.pow(2, 32) - 1, Math.pow(2, 32) - 2);  
// result2 == 2   
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]