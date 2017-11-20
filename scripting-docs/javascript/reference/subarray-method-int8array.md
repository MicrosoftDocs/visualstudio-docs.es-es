---
title: "subarray (método) (Int8Array) | Documentos de Microsoft"
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
ms.assetid: 46271ed6-a3c3-41fb-bd6f-81efa9e8dedc
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e32c3a0da7e3173273eb40bf52bb6583bd77df51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="subarray-method-int8array"></a>subarray (Método, Int8Array)
Obtiene una nueva vista Int8Array del almacén de ArrayBuffer para esta matriz, haciendo referencia a los elementos en el inicio (incluidos) hasta el final (excluidos).  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
var newInt8Array = int8Array.subset(begin, end);  
```  
  
## <a name="parameters"></a>Parámetros  
 `newInt8Array`  
 Submatriz que devuelve este método.  
  
 `begin`  
 Índice del principio de la matriz.  
  
 `end`  
 Índice del final de la matriz, sin incluir.  
  
## <a name="remarks"></a>Comentarios  
 Si el valor de begin o end es negativo, hace referencia a un índice contando desde el final de la matriz, no desde el principio. Si no se especifica el valor de end, la submatriz incluye todos los elementos desde el principio hasta el final del objeto TypedArray. El intervalo especificado por los valores de begin y end se une al intervalo de índices válido para la matriz actual. Si la longitud calculada del nuevo TypedArray fuera negativa, se fija en cero. El objeto TypedArray devuelto será del mismo tipo que la matriz en la que se invoca este método.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo obtener una submatriz de dos elementos, empezando por el primer elemento de la matriz.  
  
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
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]