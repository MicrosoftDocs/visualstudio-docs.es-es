---
title: getFloat32 (método, DataView) | Documentos de Microsoft
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
ms.assetid: adecf671-bde4-46be-a875-33b6d6e970b1
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75fc5be6d8563a44504ae2d1c7ddd9429eccb390
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636505"
---
# <a name="getfloat32-method-dataview"></a>getFloat32 (Método, DataView)
Obtiene el valor Float32 en el desplazamiento de bytes especificado desde el principio de la vista. No hay ninguna restricción de alineación; desde cualquier desplazamiento, se pueden obtener los valores de varios bytes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
var testFloat = dataView.getFloat32(byteOffset, littleEndian);   
```  
  
## <a name="parameters"></a>Parámetros  
 `testFloat`  
 Obligatorio. El valor Float32 que se devuelve desde el método.  
  
 `byteOffset`  
 El lugar en el búfer en el que se debe recuperar el valor.  
  
 `littleEndian`  
 Opcional. Si es false o no definido, se debe leer un valor de big-endian, en caso contrario, se debe leer un valor de little-endian.  
  
## <a name="remarks"></a>Comentarios  
 Estos métodos genera una excepción si se leen más allá del final de la vista.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo obtener el primer Float32 en DataView.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getFloat32(0));  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]