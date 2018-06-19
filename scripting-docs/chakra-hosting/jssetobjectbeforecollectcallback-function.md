---
title: Función JsSetObjectBeforeCollectCallback | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: ea2cbd94-d8b0-4fa9-a4a1-c75a4e338eaf
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a472e63afd909ee7bcb74cb2fdd1ae98d6a2938
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568925"
---
# <a name="jssetobjectbeforecollectcallback-function"></a>Función JsSetObjectBeforeCollectCallback
Establece una función de devolución de llamada a la que llama el runtime antes de la recolección de elementos no utilizados de un objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsSetObjectBeforeCollectCallback(  
   _In_ JsRef ref,  
   _In_opt_ void *callbackState,  
   _In_ JsObjectBeforeCollectCallback objectBeforeCollectCallback  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ref`  
 El objeto para el que se va a registrar la devolución de llamada.  
  
 `callbackState`  
 Estado proporcionado por el usuario que se pasará de nuevo a la devolución de llamada.  
  
 `objectBeforeCollectCallback`  
 La función de devolución de llamada que se establece. Utilice null para borrar la devolución de llamada registrada anteriormente.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 La devolución de llamada se invoca en el subproceso de ejecución del runtime actual, por lo que la ejecución se bloquea hasta que se complete la devolución de llamada.  
  
 Esta API solo es compatible en modo perimetral.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)