---
title: toString (método, Array) | Documentos de Microsoft
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
ms.assetid: 71fbea85-3e00-41b0-b167-25e4281e5e8a
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6dc7cbf843e47ffc2d21f5a2b1d03c43e675a130
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640415"
---
# <a name="tostring-method-array"></a>toString (Método, Array)
Devuelve una representación de cadena de una matriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
array.toString()  
```  
  
## <a name="parameters"></a>Parámetros  
 `array`  
 Obligatorio. La matriz para representar como una cadena.  
  
## <a name="return-value"></a>Valor devuelto  
 La representación de cadena de la matriz.  
  
## <a name="remarks"></a>Comentarios  
 Los elementos de un `Array` se convierten en cadenas. Las cadenas resultantes se concatenan y separadas por comas.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la **toString** método con una matriz.  
  
```JavaScript  
var arr = [1, 2, 3, 4];  
var s = arr.toString();  
document.write(s);  
  
// Output: 1,2,3,4  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]