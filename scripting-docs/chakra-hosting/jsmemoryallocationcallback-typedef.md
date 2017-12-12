---
title: "Definición de tipo JsMemoryAllocationCallback | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 511babc7-3caa-4ee5-82a2-943bbd34db8d
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9672c23f48a2cb3e20de58012b267b30f4514d66
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jsmemoryallocationcallback-typedef"></a>JsMemoryAllocationCallback (Typedef)
Rutina de devolución de llamada implementada por el usuario para los eventos de asignación de memoria.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef bool (CALLBACK * JsMemoryAllocationCallback)(  
   _In_opt_ void *callbackState,  
   _In_ JsMemoryEventType allocationEvent,  
   _In_ size_t allocationSize  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 callbackState  
 El estado pasado a JsSetRuntimeMemoryAllocationCallback.  
  
 allocationEvent  
 El tipo de evento de asignación de tipos.  
  
 allocationSize  
 El tamaño de la asignación.  
  
## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto  
 En el evento JsMemoryAllocate, si se devuelve true el runtime podrá continuar con la asignación. Si se devuelve false, quiere decir que la solicitud de asignación se ha rechazado. El valor devuelto se omite para otros eventos de asignación.  
  
## <a name="remarks"></a>Comentarios  
 Use JsSetRuntimeMemoryAllocationCallback para registrar esta devolución de llamada.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)