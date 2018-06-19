---
title: establecer el método (Int8Array) | Documentos de Microsoft
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
ms.assetid: 4beae82e-8556-48aa-86c6-18c8859d913e
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bfa9c319caf448e20888aeefa2f29aaade9aa364
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639815"
---
# <a name="set-method-int8array"></a>set (Método, Int8Array)
Establece un valor o una matriz de valores.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
int8Array.set(index, value);  
int8Array.set(array, offset);  
  
```  
  
## <a name="parameters"></a>Parámetros  
 `index`  
 Índice de la ubicación que se va a establecer.  
  
 `value`  
 El valor que se va a establecer.  
  
 `array`  
 Matriz con o sin tipo de valores que se va a establecer.  
  
 `offset`  
 Índice de la matriz actual donde deben escribirse los valores.  
  
## <a name="remarks"></a>Comentarios  
 Si la matriz de entrada es TypedArray, las dos matrices pueden utilizar el mismo ArrayBuffer subyacente. En esta situación, los valores se establecen como si todos los datos se copiasen primero en un búfer temporal que no se solapa con ninguna de las matrices y, a continuación, los datos del búfer temporal se copiasen en la matriz actual.  
  
 Si el valor de sumar el desplazamiento más la longitud de la matriz especificada está fuera de intervalo del objeto TypedArray actual, se produce una excepción.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo establecer el primer elemento de la matriz.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Int8Array(buffer.byteLength);  
            intArr.set(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]