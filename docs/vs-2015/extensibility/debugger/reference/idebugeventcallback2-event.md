---
title: IDebugEventCallback2::Event | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 37462b5f274ca6e6c2a4a2feb4083ea94ea2f066
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58996062"
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Envía una notificación de eventos de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Event(   
   IDebugEngine2*  pEngine,  
   IDebugProcess2* pProcess,  
   IDebugProgram2* pProgram,  
   IDebugThread2*  pThread,  
   IDebugEvent2*   pEvent,  
   REFIID          riidEvent,  
   DWORD           dwAttrib  
);  
```  
  
```csharp  
int Event(   
   IDebugEngine2  pEngine,  
   IDebugProcess2 pProcess,  
   IDebugProgram2 pProgram,  
   IDebugThread2  pThread,  
   IDebugEvent2   pEvent,  
   ref Guid       riidEvent,  
   uint           dwAttrib  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pEngine`  
 [in] Un [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) objeto que representa el motor de depuración (DE) que envía este evento. Se requiere a DE rellenar este parámetro.  
  
 `pProcess`  
 [in] Un [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) objeto que representa el proceso en el que se produce el evento. Este parámetro se rellena mediante el Administrador de depuración de la sesión (SDM). A DE siempre transfiere un valor null para este parámetro.  
  
 `pProgram`  
 [in] Un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa el programa en el que se produce este evento. Para la mayoría de los eventos, este parámetro no es un valor null.  
  
 `pThread`  
 [in] Un [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa el subproceso en el que se produce este evento. Para los eventos de parada, este parámetro no puede ser un valor null como el marco de pila se obtiene de este parámetro.  
  
 `pEvent`  
 [in] Un [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) objeto que representa el evento de depuración.  
  
 `riidEvent`  
 [in] GUID que identifica la interfaz de eventos que desea obtener de la `pEvent` parámetro.  
  
 `dwAttrib`  
 [in] Una combinación de marcas de la [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) enumeración.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Cuando se llama a este método, el `dwAttrib` parámetro debe coincidir con el valor devuelto de la [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) método tal como se llama en el objeto de evento pasado el `pEvent` parámetro.  
  
 Todos los eventos de depuración se registran de forma asincrónica, independientemente de si un evento en sí es asincrónico o no. Cuando a DE llama a este método, el valor devuelto no indica si se procesó el evento, sólo si se recibió el evento. De hecho, en determinadas circunstancias, el evento no se ha procesado cuando este método devuelve.  
  
## <a name="see-also"></a>Vea también  
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
