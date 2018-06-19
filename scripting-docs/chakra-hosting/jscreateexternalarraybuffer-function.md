---
title: Función JsCreateExternalArrayBuffer | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a02aaec-0f67-4bf9-b37c-71cdb1410ca4
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 95459f9a9ff676f47d56ed584ad44a30f24fd4cb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568035"
---
# <a name="jscreateexternalarraybuffer-function"></a>Función JsCreateExternalArrayBuffer
Crea un objeto `ArrayBuffer` de Javascript para obtener acceso a la memoria externa.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsCreateExternalArrayBuffer(  
  _Pre_maybenull_ _Pre_writable_byte_size_(byteLength) void *data,  
  _In_ unsigned int byteLength,  
  _In_opt_ JsFinalizeCallback finalizeCallback,  
  _In_opt_ void *callbackState,  
  _Out_ JsValueRef *result  
);  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 `data`  
 Es un puntero a la memoria externa.  
  
 `byteLength`  
 Es el número de bytes de la memoria externa.  
  
 `finalizeCallback`  
 Devolución de llamada para cuando finalice el objeto. Su valor puede ser null.  
  
 `callbackState`  
 Es el estado proporcionado por el usuario que se pasará de nuevo para finalizar la devolución de llamada.  
  
 `result`  
 El nuevo objeto `ArrayBuffer` .  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Requiere un contexto de script activo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)