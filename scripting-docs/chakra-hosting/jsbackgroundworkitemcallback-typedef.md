---
title: JsBackgroundWorkItemCallback (Typedef) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: e6db52e1-830c-46a2-b9f9-cc2d450a1da8
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c4281ae1abf1df07d4b6374b6989377c66c1fd7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24567585"
---
# <a name="jsbackgroundworkitemcallback-typedef"></a>JsBackgroundWorkItemCallback (Typedef)
Una devolución de llamada del elemento de trabajo en segundo plano.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef void (CALLBACK *JsBackgroundWorkItemCallback)(  
   _In_opt_ void *callbackData  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 callbackData  
 Argumento de datos pasado al servicio del subproceso.  
  
## <a name="remarks"></a>Comentarios  
 Este argumento se pasa al servicio del subproceso del host (si se proporciona) para permitir que el host invoque la devolución de llamada del elemento de trabajo en el subproceso en segundo plano de su elección.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)