---
title: Función JsSetProjectionEnqueueCallback | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c751ccef-20d2-4d41-9568-1c54adf47cdf
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8abdc575c5066ade4a700a0c88e09e3476a65366
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568985"
---
# <a name="jssetprojectionenqueuecallback-function"></a>Función JsSetProjectionEnqueueCallback
Establece la devolución de llamada que se va a utilizar para invocar una finalización de proyección de vuelta al subproceso requerido de los llamadores.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsSetProjectionEnqueueCallback(  
   _In_ JsProjectionEnqueueCallback projectionEnqueueCallback,  
   _In_opt_ void *projectionEnqueueContext);  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 `projectionEnqueueContext`  
 La devolución de llamada que se invocará cada vez que se produzca una finalización de proyección en un subproceso en segundo plano.  
  
 `callbackState`  
 El contexto de aplicación proporcionado a `projectionEnqueueContext`.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Requiere un contexto de script activo.  
  
 La llamada debería proceder de otro apartamento COM o de otro subproceso del mismo MTA.  
  
 Esta API solo es compatible en modo perimetral.  
  
> [!CAUTION]
>  Esta API no admite actualmente PInvoke.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)