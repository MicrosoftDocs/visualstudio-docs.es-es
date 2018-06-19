---
title: getInt32 (método, DataView) | Documentos de Microsoft
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
ms.assetid: 7a985681-ddb1-4c2b-815c-514c17392e82
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bae788801a81265d39be5ef090e5820122cbb09b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636575"
---
# <a name="getint32-method-dataview"></a>getInt32 (Método, DataView)
Obtiene el valor Int32 en el desplazamiento de bytes especificado desde el principio de la vista. No hay ninguna restricción de alineación; desde cualquier desplazamiento, se pueden obtener los valores de varios bytes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
var testInt = dataView.getInt32(byteOffset, littleEndian);   
```  
  
## <a name="parameters"></a>Parámetros  
 `testInt`  
 Obligatorio. El valor Int32 que se devuelve desde el método.  
  
 `byteOffset`  
 El lugar en el búfer en el que se debe recuperar el valor.  
  
 `littleEndian`  
 Opcional. Si es false o no definido, se debe leer un valor de big-endian, en caso contrario, se debe leer un valor de little-endian.  
  
## <a name="remarks"></a>Comentarios  
 Estos métodos genera una excepción si se leen más allá del final de la vista.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo obtener el primer Int32 en DataView.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getInt32(0));  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]