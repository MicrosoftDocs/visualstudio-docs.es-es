---
title: "Función JsGetTypedArrayInfo | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 992bc4e9-3d06-4ad2-8b6b-88a437360f81
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 44897f3960b09a110c1f1dd288f08bd5b9edc7ed
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jsgettypedarrayinfo-function"></a>JsGetTypedArrayInfo (función)
Obtiene las propiedades de una matriz con tipo se usan con frecuencia.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsGetTypedArrayInfo(  
  _In_ JsValueRef typedArray,  
  _Out_opt_ JsTypedArrayType *arrayType,  
  _Out_opt_ JsValueRef *arrayBuffer,  
  _Out_opt_ unsigned int *byteOffset,  
  _Out_opt_ unsigned int *byteLength  
);  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 `typedArray`  
 La instancia de matriz con tipo.  
  
 `arrayType`  
 Tipo de matriz.  
  
 `arrayBuffer`  
 El almacén de reserva `ArrayBuffer` de la matriz.  
  
 `byteOffset`  
 El desplazamiento en bytes desde el principio de arrayBuffer al que hace referencia a la matriz.  
  
 `byteLength`  
 Número de bytes de la matriz.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Requiere un contexto de script activo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)