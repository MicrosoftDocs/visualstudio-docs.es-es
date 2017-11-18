---
title: "setUint16 (método, DataView) | Documentos de Microsoft"
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
ms.assetid: bdf47cda-7fa5-4aaa-8aa2-8cf9a8d56cb3
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 935c117995e00284a0083a6bdf7aedfc8c51d15c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="setuint16-method-dataview"></a>setUint16 (Método, DataView)
Establece el valor de Uint16 en el desplazamiento de bytes especificado desde el principio de la vista. No hay ninguna restricción de alineación; los valores de varios bytes pueden establecerse en cualquier posición de desplazamiento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
dataView.setUint16(byteOffset, value, littleEndian);   
```  
  
## <a name="parameters"></a>Parámetros  
 `testInt`  
 Obligatorio. El valor Uint16 que se devuelve desde el método.  
  
 `value`  
 Valor que se va a establecer.  
  
 `byteOffset`  
 El lugar en el búfer en el que se debe recuperar el valor.  
  
 `littleEndian`  
 Opcional. Si es false o no definido, se debe escribir un valor de big-endian, en caso contrario, se debe escribir el valor de un little-endian.  
  
## <a name="remarks"></a>Comentarios  
 Estos métodos genera una excepción si se escriben más allá del final de la vista.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo establecer la primera Uint16 en DataView.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setUint16(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]