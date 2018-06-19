---
title: ArrayBuffer.isView (función) (ArrayBuffer) | Documentos de Microsoft
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
ms.assetid: 1887324f-892b-4fcd-ad33-748ba9517a06
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5aaae2acb38aa2f8c4b5e49ea203e86665315700
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633375"
---
# <a name="arraybufferisview-function-arraybuffer"></a>ArrayBuffer.isView (Función, ArrayBuffer)
Determina si un objeto permite ver el búfer.  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
ArrayBuffer.isView(object)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `object`  
 Obligatorio. Objeto que se va a probar.  
  
## <a name="return-value"></a>Valor devuelto  
 Es `true` si se cumple cualquiera de las condiciones siguientes:  
  
-   `object` es un objeto `DataView`.  
  
-   `object` es una matriz con tipo.  
  
 De lo contrario, el método devuelve `false`.  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se demuestra el uso de la función `isView` para probar una matriz con tipo y un objeto `DataView`.  
  
```JavaScript  
var uint = new UInt8ClampedArray(10);  
  
if(console && console.log) {  
    console.log( ArrayBuffer.isView(uint) ); // Outputs true  
{  
var dataView = new DataView(uint.buffer);  
  
if(console && console.log) {  
    console.log( ArrayBuffer.isView(dataView) ); // Outputs true.  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Uint8ClampedArray (Objeto)](../../javascript/reference/uint8clampedarray-object-javascript.md)