---
title: "subarray (método) (Uint8ClampedArray) | Documentos de Microsoft"
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
ms.assetid: 309ed9e8-5805-47ab-b3ed-501cae1323dd
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76cda8b123b02b4c19a7fd162f3bfbce4540d149
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="subarray-method-uint8clampedarray"></a>Método subarray (Uint8ClampedArray)
Obtiene un nuevo [Uint8ClampedArray](../../javascript/reference/uint8array-object.md) ver de la [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) almacenar para esta matriz, especificando los primeros y últimos miembros de la submatriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
var newUint8ClampedArray = uint8ClampedArray.subarray(begin, end);  
```  
  
## <a name="parameters"></a>Parámetros  
 `newUint8ClampedArray`  
 Obligatorio. La submatriz que devolvió este método.  
  
 `begin`  
 Opcional. El índice del principio de la matriz.  
  
 `end`  
 Opcional. Índice del final de la matriz, sin incluir.  
  
## <a name="remarks"></a>Comentarios  
 Si el valor `begin` o `end` es negativo, hace referencia a un índice contando desde el final de la matriz, no desde el principio. Si `end` no se especifica, la submatriz contiene todos los elementos desde `begin` hasta el final de la matriz con tipo. El intervalo especificado por los valores `begin` y `end` se fija en el intervalo de índices válido para la matriz actual. Si la longitud calculada de la nueva matriz con tipo fuera negativa, se fija en cero. La matriz devuelta es del mismo tipo que la matriz en la que se invoca este método.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo obtener una submatriz de dos elementos, empezando por el primer elemento de la matriz.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var intArr = new Uint8ClampedArray(buffer.byteLength);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Objeto Uint8Array](../../javascript/reference/uint8array-object.md)   
 [Objeto ArrayBuffer](../../javascript/reference/arraybuffer-object.md)   
 [Uint8ClampedArray (Objeto)](../../javascript/reference/uint8clampedarray-object-javascript.md)