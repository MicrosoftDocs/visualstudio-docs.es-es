---
title: Función Number.isInteger (número) (JavaScript) | Documentos de Microsoft
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
ms.assetid: 54fcf68c-0067-4bad-af94-d7ff8c88914a
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20e1b7b463003d3a25ef64bba793b3273371266b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638805"
---
# <a name="numberisinteger-function-number-javascript"></a>Función Number.isInteger (número) (JavaScript)
Devuelve un valor booleano que indica si un valor es un entero.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Number.isInteger(numValue)   
```  
  
## <a name="return-value"></a>Valor devuelto  
 `true` si el valor es un entero; en caso contrario, `false`.  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Se aplica a**: [número de objeto](../../javascript/reference/number-object-javascript.md)  
  
## <a name="example"></a>Ejemplo  
  
```JavaScript  
// Returns true  
Number.isInteger(100)  
Number.isInteger(-100)  
  
// Returns false  
Number.isInteger(Number.NaN)  
Number.isInteger(Infinity)  
Number.isInteger(100 / 3)  
Number.isInteger("100")  
  
```