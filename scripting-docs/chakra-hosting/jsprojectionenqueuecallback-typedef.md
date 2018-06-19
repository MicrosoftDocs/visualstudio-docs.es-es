---
title: Definición de tipo JsProjectionEnqueueCallback | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 19c1cefb-a7be-4196-b780-9fe6adf35ba5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bda4a3a80edac38ab2c3885c2256cdf9d03eb8c1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568315"
---
# <a name="jsprojectionenqueuecallback-typedef"></a>Definición de tipo de JsProjectionEnqueueCallback
La devolución de llamada de la aplicación que JsRT llama cuando una API de proyección se completa en un subproceso que no sea el original.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef void (CALLBACK *JsProjectionEnqueueCallback)(  
  _In_ JsProjectionCallback jsCallback,  
  _In_ JsProjectionCallbackContext jsContext,  
  _In_opt_ void *callbackState  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `jsCallback`  
 La devolución de llamada que se invocará en el subproceso original.  
  
 `jsContext`  
 El contexto de las aplicaciones.  
  
 `callbackState`  
 El contexto de JsRT que se debe pasar a `jsCallback`.  
  
## <a name="remarks"></a>Comentarios  
 Requiere una llamada a JsSetProjectionEnqueueCallback para recibir devoluciones de llamada.  
  
 Esta API solo es compatible en modo perimetral.  
  
## <a name="requirements"></a>Requisitos  
 jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)