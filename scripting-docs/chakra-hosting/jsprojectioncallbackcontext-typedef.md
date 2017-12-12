---
title: "Definición de tipo JsProjectionCallbackContext | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 50c705c5-664f-4a1a-92f6-4882fc718ab1
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7548dc14ab4b3dddc1633a1ba948aba564d8438a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jsprojectioncallbackcontext-typedef"></a>Definición de tipo JsProjectionCallbackContext
El contexto que se pasa a la devolución de llamada de la aplicación, JsProjectionEnqueueCallback, desde JsRT y es pasada de nuevo a JsRT en la devolución de llamada proporcionada, `JsProjectionCallback`, por parte de la aplicación en el subproceso correcto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
typedef void *JsProjectionCallbackContext;  
```  
  
## <a name="remarks"></a>Comentarios  
 Requiere que se llame a `JsSetProjectionEnqueueCallback` para recibir devoluciones de llamada.  
  
 Esta API solo es compatible en modo perimetral.  
  
## <a name="requirements"></a>Requisitos  
 jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)