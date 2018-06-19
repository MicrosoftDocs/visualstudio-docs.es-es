---
title: Función JsCreateRuntime | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsCreateRuntime
helpviewer_keywords:
- JsCreateRuntime function
ms.assetid: 92d09b89-6593-4d73-a562-88f9fec10228
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93a3df1e7ea76cf76fad9ffde9ccea19f2ba28af
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568145"
---
# <a name="jscreateruntime-function"></a>JsCreateRuntime (Función)
Crea un runtime nuevo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
// Edge mode signature  
STDAPI_(JsErrorCode) JsCreateRuntime(  
   _In_ JsRuntimeAttributes attributes,  
   _In_opt_ JsThreadServiceCallback threadService,  
   _Out_ JsRuntimeHandle *runtime);  
  
// Legacy mode signature  
STDAPI_(JsErrorCode) JsCreateRuntime(  
   _In_ JsRuntimeAttributes attributes,  
   _In_ JsRuntimeVersion version,  
   _In_opt_ JsThreadServiceCallback threadService,  
   _Out_ JsRuntimeHandle *runtime  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `attributes`  
 Los atributos del runtime que se va a crear.  
  
 `version`  
 La versión del runtime que se va a crear.  
  
 `threadService`  
 El servicio del subproceso para el runtime. Puede ser NULL.  
  
 `runtime`  
 El runtime creado.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El parámetro `version` no es compatible con el modo de borde. Para obtener más información sobre el uso de esta API en el modo de borde, vea [Compatibilidad con motores de borde o motores heredados](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)