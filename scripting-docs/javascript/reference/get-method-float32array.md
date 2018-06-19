---
title: Get (método) (Float32Array) | Documentos de Microsoft
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
ms.assetid: f859481c-0bb8-43d3-9d54-38d303e44397
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea17b3d26a1f192843a2fb9d2d87f62fe26fceff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636545"
---
# <a name="get-method-float32array"></a>get (Método, Float32Array)
Se puede omitir. Obtiene el elemento en el índice especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
var value = float32Array.get(index);  
```  
  
## <a name="parameters"></a>Parámetros  
 `value`  
 Valor devuelto por este método.  
  
 `index`  
 Índice donde se obtendrá el elemento de la matriz.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo obtener el primer elemento de la matriz.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var floatArr = new Float32Array(buffer.byteLength / 4);  
            var element = floatArr.getFloat32(0);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]