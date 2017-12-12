---
title: JsBeforeCollectCallback (Typedef ) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 58bece47-4e6d-49e7-a93d-b6a8f9928b41
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 50e2b79ceb2809aee0348bae594e8494596b6089
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jsbeforecollectcallback-typedef"></a>JsBeforeCollectCallback (Typedef)
Una devolución de llamada que se llamó antes de la colección.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef void (CALLBACK *JsBeforeCollectCallback)(  
_In_opt_ void *callbackState  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 callbackState  
 El estado pasado a JsSetBeforeCollectCallback.  
  
## <a name="remarks"></a>Comentarios  
 Use JsSetBeforeCollectCallback para registrar esta devolución de llamada.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)