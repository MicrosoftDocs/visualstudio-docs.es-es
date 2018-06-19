---
title: setUint32 (método, DataView) | Documentos de Microsoft
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
ms.assetid: ab2894fe-4cdc-40c8-9503-951e42ca61e7
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4e4d2bf075c46f84c75a174b0ca5954b9cedf154
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639445"
---
# <a name="setuint32-method-dataview"></a>setUint32 (Método, DataView)
Establece el valor de Uint32 en el desplazamiento de bytes especificado desde el principio de la vista. No hay ninguna restricción de alineación; los valores de varios bytes pueden establecerse en cualquier posición de desplazamiento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
dataView.setUint32 (byteOffset, value, littleEndian);   
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
 En el ejemplo siguiente se muestra cómo establecer la primera Uint32 en DataView.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setUint32(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]