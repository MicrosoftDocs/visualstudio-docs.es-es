---
title: "Función JsSetRuntimeMemoryLimit | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsSetRuntimeMemoryLimit
helpviewer_keywords: JsSetRuntimeMemoryLimit function
ms.assetid: 74feb31f-19f6-43e3-b117-0694c59ac593
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 587eb369e6971c7527177624ccf5baf839246cf9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jssetruntimememorylimit-function"></a>JsSetRuntimeMemoryLimit (Función)
Establece el límite de memoria actual para un runtime.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeMemoryLimit(  
   _In_ JsRuntimeHandle runtime,  
   _In_ size_t memoryLimit  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `runtime`  
 El runtime cuyo límite de memoria se va a establecer.  
  
 `memoryLimit`  
 El nuevo límite de memoria del runtime, en bytes, o -1 para no establecer ningún límite de memoria.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El límite de memoria hará que cualquier operación que lo supere produzca un error de memoria insuficiente. Establezca el límite de memoria para el runtime en -1 si desea que este no tenga ningún límite de memoria. Los nuevos runtime no tendrán límite de memoria de forma predeterminada. Si el nuevo límite de memoria supera el uso actual, la llamada se realizará correctamente y las asignaciones futuras de este runtime producirán un error hasta que el uso de memoria del runtime descienda por debajo del límite.  
  
 El límite de memoria de un runtime se puede establecer siempre, independientemente de si el runtime está activo en otro subproceso.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)