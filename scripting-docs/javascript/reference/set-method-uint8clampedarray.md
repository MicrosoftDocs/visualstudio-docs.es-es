---
title: establecer el método (Uint8ClampedArray) | Documentos de Microsoft
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
ms.assetid: 1298443d-5c4c-4329-9ad2-35e213dca157
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed7635559e615746c577560f1a9266b26acd959d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639475"
---
# <a name="set-method-uint8clampedarray"></a>Método set (Uint8ClampedArray)
Establece un valor o una matriz de valores.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
uint8ClampedArray.set(index, value);  
uint8ClampedArray.set(array, offset);  
  
```  
  
## <a name="parameters"></a>Parámetros  
 `index`  
 Índice de la ubicación que se va a establecer.  
  
 `value`  
 El valor que se va a establecer.  
  
 `array`  
 Matriz con o sin tipo de valores que se va a establecer.  
  
 `offset`  
 Índice de la matriz actual donde deben escribirse los valores.  
  
## <a name="remarks"></a>Comentarios  
 Si la matriz de entrada es una matriz con tipo, las dos matrices pueden utilizar el mismo subyacente [ArrayBuffer](../../javascript/reference/arraybuffer-object.md). En esta situación, los valores se establecen como si todos los datos se hubiesen copiado primero en un búfer temporal que no se solapa con ninguna de las matrices y, a continuación, los datos del búfer temporal se copiasen en la matriz actual.  
  
 Si el valor de sumar el desplazamiento más la longitud de la matriz especificada está fuera de intervalo de la matriz con tipo actual, se produce una excepción.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo establecer el primer elemento de la matriz.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Uint8ClampedArray(buffer.byteLength);  
            intArr.set(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Objeto ArrayBuffer](../../javascript/reference/arraybuffer-object.md)   
 [Uint8ClampedArray (Objeto)](../../javascript/reference/uint8clampedarray-object-javascript.md)