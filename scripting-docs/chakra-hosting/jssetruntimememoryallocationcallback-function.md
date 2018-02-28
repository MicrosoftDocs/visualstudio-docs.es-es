---
title: "Función JsSetRuntimeMemoryAllocationCallback | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsSetRuntimeMemoryAllocationCallback
helpviewer_keywords:
- JsSetRuntimeMemoryAllocationCallback function
ms.assetid: 6aa7d58d-6456-4df1-815f-1ba36fb4ae14
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 755ab36c8edb8c0350eb2b245e060344c8825dee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jssetruntimememoryallocationcallback-function"></a>JsSetRuntimeMemoryAllocationCallback (Función)
Establece una devolución de llamada de asignación de memoria para el runtime especificado  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeMemoryAllocationCallback(  
   _In_ JsRuntimeHandle runtime,  
   _In_opt_ void *callbackState,  
   _In_ JsMemoryAllocationCallback allocationCallback  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `runtime`  
 El runtime para el que se va a registrar la devolución de llamada de asignación.  
  
 `callbackState`  
 Estado proporcionado por el usuario que se pasará de nuevo a la devolución de llamada.  
  
 `allocationCallback`  
 Devolución de asignación de memoria que se va a llamar para los eventos de asignación de memoria.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El registro de una devolución de llamada de asignación de memoria hará que el runtime devuelva la llamada al host siempre que adquiera o libere memoria del sistema operativo. Se llama a la rutina de devolución de llamada antes de que el administrador de memoria del runtime asigne un bloque de memoria. La asignación será rechazada si la devolución de llamada devuelve false. El administrador de memoria del runtime también invocará a la rutina de devolución de llamada después de liberar un bloque de memoria, así como después de que se produzcan errores de asignación.  
  
 La devolución de llamada se invoca en el subproceso de ejecución del runtime actual, por lo que la ejecución se bloquea hasta que se complete la devolución de llamada.  
  
 El valor devuelto de la devolución de llamada no se almacena; las asignaciones rechazadas previamente no impedirán que el runtime invoque de nuevo a la devolución de llamada más adelante para nuevas asignaciones de memoria.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)