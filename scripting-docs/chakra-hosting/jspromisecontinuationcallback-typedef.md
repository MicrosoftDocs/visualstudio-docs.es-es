---
title: Definición de tipos JsPromiseContinuationCallback | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 51a3fd02-9668-4cf7-bb0b-e1fd03b2528f
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 762391cb66e5298bd70beb3238720d3717554ae0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568605"
---
# <a name="jspromisecontinuationcallback-typedef"></a>Definición de tipo JsPromiseContinuationCallback
Una devolución de llamada de la continuación de compromiso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef void (CALLBACK *JsPromiseContinuationCallback)(  
  _In_ JsValueRef task,  
  _In_opt_ void *callbackState  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `task`  
  `callbackState`  
  
## <a name="remarks"></a>Comentarios  
 El host puede especificar una devolución de llamada de continuación de compromiso en `JsSetPromiseContinuationCallback`. Si un script crea una tarea para que se ejecute más tarde, se llamará a la devolución de llamada de continuación de compromiso con la tarea y la tarea deberá colocarse en una cola FIFO, que se ejecutará cuando se acabe de ejecutar el script actual.  
  
 Esta API solo es compatible en modo perimetral.  
  
## <a name="requirements"></a>Requisitos  
 jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)