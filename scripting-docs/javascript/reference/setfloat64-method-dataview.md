---
title: setFloat64 (método, DataView) | Documentos de Microsoft
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
ms.assetid: 63d2c631-876f-4d4b-b3b6-62b0aaffe6c5
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e22552e4190c74b520dfce853be6e9d1364764e3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639965"
---
# <a name="setfloat64-method-dataview"></a>setFloat64 (Método, DataView)
Establece el valor Float64 en el desplazamiento de bytes especificado desde el principio de la vista. No hay ninguna restricción de alineación; los valores de varios bytes pueden establecerse en cualquier posición de desplazamiento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
dataView.setFloat64 (byteOffset, value, littleEndian);   
```  
  
## <a name="parameters"></a>Parámetros  
 `byteOffset`  
 El lugar en el búfer en el que se debe recuperar el valor.  
  
 `value`  
 Valor que se va a establecer.  
  
 `littleEndian`  
 Opcional. Si es false o no definido, se debe escribir un valor de big-endian, en caso contrario, se debe escribir el valor de un little-endian.  
  
## <a name="remarks"></a>Comentarios  
 Estos métodos genera una excepción si se escriben más allá del final de la vista.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo establecer la primera Float64 en DataView.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setFloat64(0, 9.1);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]