---
title: getInt16 (método, DataView) | Documentos de Microsoft
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
ms.assetid: d364cbe0-48a6-4350-a6ca-9f563d7ae571
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a30804ddaa4840bfbd8a791ac5a5d4d82d107879
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636535"
---
# <a name="getint16-method-dataview"></a>getInt16 (Método, DataView)
Obtiene el valor de tipo Int16 en el desplazamiento de bytes especificado desde el principio de la vista. No hay ninguna restricción de alineación; desde cualquier desplazamiento, se pueden obtener los valores de varios bytes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
var testInt = dataView.getInt16(byteOffset, littleEndian);   
```  
  
## <a name="parameters"></a>Parámetros  
 `testInt`  
 Obligatorio. El valor de tipo Int16 que se devuelve desde el método.  
  
 `byteOffset`  
 El lugar en el búfer en el que se debe recuperar el valor.  
  
 `littleEndian`  
 Opcional. Si es false o no definido, se debe leer un valor de big-endian, en caso contrario, se debe leer un valor de little-endian.  
  
## <a name="remarks"></a>Comentarios  
 Estos métodos genera una excepción si se leen más allá del final de la vista.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo obtener el primer Int16 en DataView.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getInt16(0));  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]