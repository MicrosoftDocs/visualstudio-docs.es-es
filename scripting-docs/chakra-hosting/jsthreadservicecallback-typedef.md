---
title: Definición de tipo JsThreadServiceCallback | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: dbe67be5-418a-4f66-8b68-b38078a6d140
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c4b7ea4d0d5eaba17269a1777cdf96b5a2a5cda3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568775"
---
# <a name="jsthreadservicecallback-typedef"></a>JsThreadServiceCallback (Typedef)
Devolución de llamada del servicio del subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef bool (CALLBACK *JsThreadServiceCallback)(  
   _In_ JsBackgroundWorkItemCallback callback,  
   _In_opt_ void *callbackData  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 callback  
 La devolución de llamada para el elemento de trabajo en segundo plano.  
  
 callbackData  
 El argumento de datos que se va a pasar a la devolución de llamada.  
  
## <a name="remarks"></a>Comentarios  
 El host puede especificar un servicio del subproceso en segundo plano al llamar a JsCreateRuntime. Si se especifica, los elementos de trabajo en segundo plano se pasarán al host usando esta devolución de llamada. Se espera que el host inicie la ejecución del elemento de trabajo en segundo plano inmediatamente y devuelva true, o que devuelva false, con lo que el runtime controlará el elemento de trabajo desde el subproceso.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)