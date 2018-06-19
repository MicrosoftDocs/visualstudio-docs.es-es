---
title: Función Number.isNaN (número) (JavaScript) | Documentos de Microsoft
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
ms.assetid: 2d9813d6-ec9c-433b-b060-8e3c3ff62ca4
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c11abe2dd2fc70431800d31f4c44279a88cd75d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639065"
---
# <a name="numberisnan-function-number-javascript"></a>Función Number.isNaN (número) (JavaScript)
Devuelve un valor booleano que indica si un valor es el valor reservado `NaN` (no un número).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Number.isNaN(numValue)   
```  
  
#### <a name="parameters"></a>Parámetros  
 `numValue`  
 Obligatorio. Valor que se va a probar con `NaN`.  
  
## <a name="return-value"></a>Valor devuelto  
 `true` si el valor convertido al tipo `Number` es `NaN`; en caso contrario, `false`.  
  
## <a name="remarks"></a>Comentarios  
 Este método suele usarse para probar los valores devueltos desde los métodos `parseInt` y `parseFloat`.  
  
 `Number.isNaN` corrige los problemas con la función `isNaN` global. `Number.isNaN` solo convierte su argumento en el tipo Number después de compararlo con `NaN`. Por tanto, devolverá `true` solo si el argumento pasado es exactamente el mismo valor que `NaN`. La función `isNaN` global convierte su argumento en el tipo Number antes de la comparación, que puede dar lugar a valores que no son de número que devuelven `true`, mientras que podrían no devolver `true` para `Number.isNaN`.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Se aplica a**: [número de objeto](../../javascript/reference/number-object-javascript.md)  
  
## <a name="example"></a>Ejemplo  
  
```JavaScript  
// Returns true.  
Number.isNaN(NaN);  
Number.isNaN(Number.NaN);  
Number.isNaN(0 / 0);  
  
// Returns false.  
Number.isNaN(100);  
// Returns false.  
// Strings are converted to numbers and return false.  
Number.isNaN("100");  
Number.isNaN("ABC");  
Number.isNaN("10C");  
Number.isNaN("abc123");  
  
```