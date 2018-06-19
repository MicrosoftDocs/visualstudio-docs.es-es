---
title: byteLength (propiedad, DataView) | Documentos de Microsoft
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
ms.assetid: 6274285f-b673-48f6-a1e7-89ff7ee348b5
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2a9eb55a40722c42ccc9711c434061e98b64039
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633555"
---
# <a name="bytelength-property-dataview"></a>byteLength (Propiedad, DataView)
Sólo lectura. Longitud de esta vista desde el principio de su ArrayBuffer, en bytes, corregida en tiempo de construcción.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
var byteLength = dataView.byteLength;  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo obtener la longitud de un DataView desde un XMLHttpRequest.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.byteLength);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]