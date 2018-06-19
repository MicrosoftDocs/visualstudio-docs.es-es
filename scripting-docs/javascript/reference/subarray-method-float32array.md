---
title: subarray (método) (Float32Array) | Documentos de Microsoft
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
ms.assetid: 97aa27c0-d650-411e-b929-dd9c4a2ae9a5
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 78d8c729298fe80d841d7c4750e4e6817120c9d3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639875"
---
# <a name="subarray-method-float32array"></a>subarray (Método, Float32Array)
Obtiene una nueva vista de Float32Array de la [objeto ArrayBuffer](../../javascript/reference/arraybuffer-object.md) almacenar para esta matriz, especificando los primeros y últimos miembros de la submatriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
var newFloat32Array = float32Array.subarray(begin, end);  
```  
  
## <a name="parameters"></a>Parámetros  
 `newFloat32Array`  
 Submatriz que devuelve este método.  
  
 `begin`  
 Índice del principio de la matriz.  
  
 `end`  
 Índice del final de la matriz,  
  
## <a name="remarks"></a>Comentarios  
 Si el valor `begin` o `end` es negativo, hace referencia a un índice contando desde el final de la matriz, no desde el principio. Si `end` no se especifica, la submatriz contiene todos los elementos desde `begin` hasta el final de la matriz con tipo. El intervalo especificado por los valores `begin` y `end` se fija en el intervalo de índices válido para la matriz actual. Si la longitud calculada de la nueva matriz con tipo fuera negativa, se fija en cero. La matriz devuelta será del mismo tipo que la matriz en la que se invoca este método.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo obtener una submatriz de tres elementos, empezando por el primer elemento de la matriz.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var floatArr = new Float32Array(buffer.byteLength / 4);  
            var subArr = floatArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]