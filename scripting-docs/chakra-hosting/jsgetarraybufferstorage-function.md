---
title: "Función JsGetArrayBufferStorage | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 712ae298-36a9-47ef-b089-e51835c056bc
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a667325eb4d1d9540751a52232e5e06b3004b8b5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jsgetarraybufferstorage-function"></a>Función JsGetArrayBufferStorage
Obtiene el almacenamiento de memoria subyacente utilizado por un `ArrayBuffer`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
JsErrorCode STDAPI_ JsGetArrayBufferStorage(  
   _In_ JsValueRef arrayBuffer,  
   _Outptr_result_bytebuffer_(*bufferLength) BYTE **buffer,  
   _Out_ unsigned int *bufferLength  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `arrayBuffer`  
 La instancia de ArrayBuffer.  
  
 `buffer`  
 El búfer de ArrayBuffer. La duración del búfer devuelto es la misma que la duración del `ArrayBuffer`. El puntero de búfer no se considera una referencia al `ArrayBuffer` para la recolección de elementos no utilizados.  
  
 `bufferLength`  
 El número de bytes en el búfer.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Requiere un contexto de script activo.  
  
 Esta API solo es compatible en modo perimetral.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)