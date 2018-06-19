---
title: establecer el método (Uint32Array) | Documentos de Microsoft
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
ms.assetid: 00f521b2-db27-45ec-bdee-2891983618b9
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c28d4b8415ef9bab56e3aa0937b051ceb6989f75
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639515"
---
# <a name="set-method-uint32array"></a>set (Método, Uint32Array)
Establece un valor o una matriz de valores.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
uint32Array.set(index, value);  
uint32Array.set(array, offset);  
  
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
            var intArr = new Uint32Array(buffer.byteLength / 4);  
            intArr.set(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]