---
title: "parseInt (función) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: parseInt
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: parseInt method
ms.assetid: e86471af-2a0e-4359-83af-f1ac81e51421
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 54ee77470d32410ae46a628d54fc3bda97fecc51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="parseint-function-javascript"></a>parseInt (Función de JavaScript)
Convierte una cadena en un entero.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
parseInt(numString, [radix])   
```  
  
## <a name="parameters"></a>Parámetros  
 `numString`  
 Obligatorio. Una cadena para convertir en un número.  
  
 `radix`  
 Opcional. Un valor entre 2 y 36 que especifica la base del número de `numString`. Si no se proporciona este argumento, las cadenas con el prefijo '0 x' se consideran hexadecimales. Todas las demás cadenas se consideran decimales.  
  
## <a name="remarks"></a>Comentarios  
 El `parseInt` función devuelve un valor entero igual al número contenido en `numString`. Si ningún prefijo de `numString` se puede analizar correctamente en un entero, `NaN` (no un número) se devuelve.  
  
```JavaScript  
parseInt("abc");     // Returns NaN.  
parseInt("12abc");   // Returns 12.  
```  
  
 Puede probar para `NaN` mediante el `isNaN` función.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Global (objeto)](../../javascript/reference/global-object-javascript.md)  
  
> [!NOTE]
>  A partir de [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)], el `parseInt` función no tratar una cadena que contiene un prefijo de '0' como un octal. Cuando no se utiliza la `parseInt` de función, sin embargo, las cadenas con un prefijo de '0' aún se pueden interpretar como octales. Vea [tipos de datos](../../javascript/data-types-javascript.md) para obtener información acerca de enteros octales.  
  
## <a name="see-also"></a>Vea también  
 [isNaN (función)](../../javascript/reference/isnan-function-javascript.md)   
 [parseFloat (función)](../../javascript/reference/parsefloat-function-javascript.md)   
 [String (objeto)](../../javascript/reference/string-object-javascript.md)   
 [valueOf (Método, Object)](../../javascript/reference/valueof-method-object-javascript.md)