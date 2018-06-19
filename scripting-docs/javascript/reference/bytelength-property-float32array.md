---
title: byteLength propiedad (Float32Array) | Documentos de Microsoft
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
ms.assetid: ea55beb2-e79f-4706-bcc9-6fdbf89e0fe9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1c4b403a6632b143961df541dc13b03c9208d274
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633565"
---
# <a name="bytelength-property-float32array"></a>byteLength (Propiedad, Float32Array)
Sólo lectura. Longitud de esta matriz desde el principio de su ArrayBuffer, en bytes, corregida en tiempo de construcción.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
var arrayByteLength = float32Array.byteLength;  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo obtener la longitud de la matriz.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var floatArr = new Float32Array(buffer.byteLength) / 4);  
            alert(floatArr.byteLength);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]