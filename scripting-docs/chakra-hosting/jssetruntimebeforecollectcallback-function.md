---
title: Función JsSetRuntimeBeforeCollectCallback | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsSetRuntimeBeforeCollectCallback
helpviewer_keywords:
- JsSetRuntimeBeforeCollectCallback function
ms.assetid: 7b2fb911-6007-4ed9-a307-66cefe590ea4
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 469b33a324f67d17bd6f5156da7cce169b98c663
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568995"
---
# <a name="jssetruntimebeforecollectcallback-function"></a>JsSetRuntimeBeforeCollectCallback (Función)
Establece una función de devolución de llamada a la que llama el runtime antes de la recolección de elementos no utilizados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeBeforeCollectCallback(  
   _In_ JsRuntimeHandle runtime,  
   _In_opt_ void *callbackState,  
   _In_ JsBeforeCollectCallback beforeCollectCallback  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `runtime`  
 El runtime para el que se va a registrar la devolución de llamada de asignación.  
  
 `callbackState`  
 Estado proporcionado por el usuario que se pasará de nuevo a la devolución de llamada.  
  
 `beforeCollectCallback`  
 La función de devolución de llamada que se establece.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 La devolución de llamada se invoca en el subproceso de ejecución del runtime actual, por lo que la ejecución se bloquea hasta que se complete la devolución de llamada.  
  
 La devolución de llamada pueden usarla los hosts para preparar la recolección de elementos no utilizados. Por ejemplo, liberando referencias innecesarias en los objetos de Chakra.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)