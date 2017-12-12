---
title: "Función JsCreateTypedArray | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 937a2a91-6f5f-4aaa-a018-d3089702bf36
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1df33d0e1aadec9d7ed5aebf743e2c2f840e51fd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jscreatetypedarray-function"></a>Función JsCreateTypedArray
Crea un objeto de matriz con tipo de JavaScript.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
STDAPI_(JsErrorCode) JsCreateTypedArray(  
   _In_ JsTypedArrayType arrayType,  
   _In_ JsValueRef baseArray,  
   _In_ unsigned int byteOffset,  
   _In_ unsigned int elementLength,  
   _Out_ JsValueRef *result  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `arrayType`  
 El tipo de la matriz que se va a crear.  
  
 `baseArray`  
 La matriz base de la nueva matriz. Utilice `JS_INVALID_REFERENCE` si no hay matriz base.  
  
 `byteOffset`  
 Desplazamiento en bytes desde el principio de `baseArray` (`ArrayBuffer`) de la matriz con tipo de resultado a la que se va a hacer referencia. Solo se aplica cuando `baseArray` es un objeto `ArrayBuffer`. De lo contrario, debe ser 0.  
  
 `elementLength`  
 Número de elementos de la matriz. Solo se aplica cuando se crea una nueva matriz con tipo sin `baseArray` (`baseArray` es `JS_INVALID_REFERENCE`) o cuando `baseArray` es un objeto `ArrayBuffer`. De lo contrario, debe ser 0.  
  
 `result`  
 El nuevo objeto de matriz con tipo.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 La `baseArray` puede ser una `ArrayBuffer`, otra matriz con tipo o una `Array` de JavaScript. La matriz con tipo devuelta utilizará `baseArray` si se trata de `ArrayBuffer`, o en caso contrario, creará y usará una copia de la matriz de origen subyacente.  
  
 Requiere un contexto de script activo.  
  
 Esta API solo es compatible en modo perimetral.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)