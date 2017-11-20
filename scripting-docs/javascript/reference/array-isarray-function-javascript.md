---
title: "Array.isArray (función) (JavaScript) | Documentos de Microsoft"
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
helpviewer_keywords:
- isArray function [JavaScript]
- Array.isArray function [JavaScript]
ms.assetid: 58f7d2e0-d310-4292-b9bc-37a73c585780
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c31bdfe022cd41648117fc80c8df257e48e592ae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="arrayisarray-function-javascript"></a>Array.isArray (Función de JavaScript)
Determina si un objeto es una matriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Array.isArray(object)   
```  
  
#### <a name="parameters"></a>Parámetros  
 `object`  
 Obligatorio. Objeto que se va a probar.  
  
## <a name="return-value"></a>Valor devuelto  
 Es `true` si `object` es una matriz; en caso contrario, es `false`. Si el argumento `object` no es un objeto, se devuelve `false`.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra el uso de la función `Array.isArray`.  
  
```JavaScript  
var ar = [];  
var result = Array.isArray(ar);  
// Output: true  
  
var ar = new Array();  
var result = Array.isArray(ar);  
// Output: true  
  
var ar = [1, 2, 3];  
var result = Array.isArray(ar);  
// Output: true  
  
var result = Array.isArray("an array");  
document.write(result);  
// Output: false  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Array (objeto)](../../javascript/reference/array-object-javascript.md)   
 [Usar matrices](../../javascript/advanced/using-arrays-javascript.md)   
 [typeof (Operador)](../../javascript/reference/typeof-operator-decrementjavascript.md)