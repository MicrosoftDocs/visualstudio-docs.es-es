---
title: Función JsCreateArrayBuffer | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c9e74184-7dd9-41a7-a1fe-9575e1701392
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9fa67e924b56bea2b4cb1f6d9257ed234e1ea77
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24567675"
---
# <a name="jscreatearraybuffer-function"></a>Función JsCreateArrayBuffer
Crea un objeto `ArrayBuffer` de JavaScript.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsCreateArrayBuffer(  
   _In_ unsigned int byteLength,  
   _Out_ JsValueRef *result  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `byteLength`  
 El número de bytes del ArrayBuffer.  
  
 `result`  
 El nuevo objeto ArrayBuffer.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Requiere un contexto de script activo.  
  
 Esta API solo es compatible en modo perimetral.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)