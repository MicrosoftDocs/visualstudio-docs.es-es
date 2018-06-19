---
title: Definición de tipo JsProjectionCallback | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 32f22d37-e57e-4196-b6cd-a3fc75bd0632
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 80d1c64f04f44a8560c25935fba2a48905a73260
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568255"
---
# <a name="jsprojectioncallback-typedef"></a>Definición de tipo de JsProjectionCallback
La devolución de llamada de JsRT debería llamarse con el contexto pasado a `JsProjectionEnqueueCallback` en el subproceso correcto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef void (CALLBACK *JsProjectionCallback)(  
  _In_ JsProjectionCallbackContext jsContext  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `jsContext`  
 Requiere que se llame a `JsSetProjectionEnqueueCallback` para recibir devoluciones de llamada.  
  
## <a name="remarks"></a>Comentarios  
 Esta API solo es compatible en modo perimetral.  
  
## <a name="requirements"></a>Requisitos  
 jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)