---
title: getInt8 (método, DataView) | Documentos de Microsoft
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
ms.assetid: 867eefa0-f2e0-44b9-85bc-efb849d55138
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4963cb1b407b964b082daa10660fe812dcb700b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636525"
---
# <a name="getint8-method-dataview"></a>getInt8 (Método, DataView)
Obtiene el valor Int8 en el desplazamiento de bytes especificado desde el principio de la vista. No hay ninguna restricción de alineación; desde cualquier desplazamiento, se pueden obtener los valores de varios bytes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
var testInt = dataView.getInt8(byteOffset);   
```  
  
## <a name="parameters"></a>Parámetros  
 `testInt`  
 Obligatorio. El valor Int8 que se devuelve desde el método.  
  
 `byteOffset`  
 El lugar en el búfer en el que se debe recuperar el valor.  
  
## <a name="remarks"></a>Comentarios  
 Estos métodos genera una excepción si se leen más allá del final de la vista.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo obtener el primer Int8 en DataView.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getInt8(0));  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]