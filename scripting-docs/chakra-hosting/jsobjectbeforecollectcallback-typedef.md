---
title: Definición de tipo JsObjectBeforeCollectCallback | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: f21a064a-579f-44cb-9d21-76b62e8c18f5
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7d11de01c44792d3e41cc2721a404f2ed906f02e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568445"
---
# <a name="jsobjectbeforecollectcallback-typedef"></a>Definición de tipo de JsObjectBeforeCollectCallback
Una devolución de llamada a la que se llamó antes de recopilar un objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef void (CALLBACK *JsObjectBeforeCollectCallback)(  
  _In_ JsRef ref,  
  _In_opt_ void *callbackState  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ref`  
 El objeto que se va a recopilar.  
  
 `callbackState`  
 El estado pasado a `JsSetObjectBeforeCollectCallback`.  
  
## <a name="remarks"></a>Comentarios  
 Esta API solo es compatible en modo perimetral.  
  
## <a name="requirements"></a>Requisitos  
 jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)