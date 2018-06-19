---
title: slice (método, ArrayBuffer) | Documentos de Microsoft
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
ms.assetid: 2dcc51ff-f444-4d51-80ba-3bcd845ba0ae
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25fc10a02b4a3422a6720ad91c8bba29906da0e5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640495"
---
# <a name="slice-method-arraybuffer"></a>slice (Método, ArrayBuffer)
Devuelve una sección de un [ArrayBuffer](../../javascript/reference/arraybuffer-object.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
arrayBufferObj.slice(start, [end])   
```  
  
## <a name="parameters"></a>Parámetros  
 `arrayBufferObj`  
 Obligatorio. El [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) se copiará la sección desde el objeto.  
  
 `start`  
 Obligatorio. Índice de bytes del principio de la sección que se copiará.  
  
 `end`  
 Opcional. Índice de bytes del final de la sección que se copiará.  
  
## <a name="remarks"></a>Comentarios  
 El `slice` método devuelve un [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) objeto que contiene la parte especificada de `arrayBufferObj`.  
  
 El método `slice` se copia hasta el byte indicado en `end` (no inclusive). Si `start` o `end` es negativo, se trata como el índice especificado `length`  +  `start` o `end`, respectivamente, donde `length` es la longitud de la [ArrayBuffer](../../javascript/reference/arraybuffer-object.md). Si se omite `end`, la extracción continúa hasta el final de `arrayBufferObj`. Si `end` se produce antes de `start`, ningún byte se copia al nuevo [ArrayBuffer](../../javascript/reference/arraybuffer-object.md).  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo, se muestra cómo utilizar el método `slice`.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer1 = req.response;  
            var buffer2 = buffer1.slice(40, 48);  
            var dataview = new DataView(buffer2);  
            var ints = new Int32Array(buffer2.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[1]);  
        }  
    }  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [ArrayBuffer (Objeto)](../../javascript/reference/arraybuffer-object.md)