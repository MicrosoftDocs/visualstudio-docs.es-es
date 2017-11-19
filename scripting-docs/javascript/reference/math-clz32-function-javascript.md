---
title: "Math.clz32 (función de JavaScript) | Documentos de Microsoft"
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
ms.assetid: 34615d7a-6d88-4ab5-a696-7e496caa51db
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 511f407acc327a32ed6c53c12283503e20b514fe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="mathclz32-function-javascript"></a>Math.clz32 (función de JavaScript)
Devuelve el número de bits significativos de valor cero en la representación binaria de 32 bits de un número.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Math.clz32(  
number  
)   
```  
  
## <a name="remarks"></a>Comentarios  
 Si `number` es 0, el resultado será 32. Si el bit más significativo de la codificación binaria de 32 bits de `number` es 1, el resultado será 0.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Se aplica a**: [Math (objeto)](../../javascript/reference/math-object-javascript.md)