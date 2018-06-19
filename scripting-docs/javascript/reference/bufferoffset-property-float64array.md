---
title: bufferOffset propiedad (Float64Array) | Documentos de Microsoft
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
ms.assetid: 9b566ec9-97d1-4a54-96cd-c1608f0ed330
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2d64af7d1f7aeb9f4f42ee1854c5a6a93ad5505
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633425"
---
# <a name="bufferoffset-property-float64array"></a>bufferOffset (Propiedad, Float64Array)
Sólo lectura. Desplazamiento de esta matriz desde el principio de su ArrayBuffer, en bytes, corregido en tiempo de construcción.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
var arrayOffset = float64Array.byteOffset;  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo obtener el desplazamiento de la matriz.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var floatArr = new Float64Array(buffer.byteLength / 8);  
            alert(floatArr.byteOffset);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]