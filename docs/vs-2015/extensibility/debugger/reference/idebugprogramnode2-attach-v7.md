---
title: IDebugProgramNode2::Attach_V7 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
ms.assetid: b5ffc736-efc7-4ca8-964d-5536ff891b0e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 08028f2b03f3ea36cc72172ca8f9de31740b49f3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63417907"
---
# <a name="idebugprogramnode2attachv7"></a>IDebugProgramNode2::Attach_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

EN DESUSO. NO USE.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Attach_V7 (   
   IDebugProgram2*       pMDMProgram,  
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason  
);  
```  
  
```csharp  
int Attach_V7 (   
   IDebugProgram2       pMDMProgram,  
   IDebugEventCallback2 pCallback,  
   uint                 dwReason  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pMDMProgram`  
 [in] El [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaz que representa el programa para adjuntar a.  
  
 `pCallback`  
 [in] El [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) interfaz que se usará para enviar eventos de depuración para el SDM.  
  
 `dwReason`  
 [in] Un valor de la [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) enumeración que especifica la razón para adjuntar.  
  
## <a name="return-value"></a>Valor devuelto  
 Siempre debe devolver una implementación `E_NOTIMPL`.  
  
## <a name="remarks"></a>Comentarios  
  
> [!WARNING]
> Como de [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], este método ya no se usa y siempre debe devolver `E_NOTIMPL`. Consulte la [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interfaz para un enfoque alternativo si el nodo del programa debe indicar no se puede adjuntar a o si el nodo del programa es simplemente la configuración del programa `GUID`. En caso contrario, implemente el [adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md) método.  
  
## <a name="prior-to-visual-studio-2005"></a>Antes de Visual Studio 2005  
 Este método debe implementarse solo si la DE que se ejecuta en el espacio de direcciones del programa que se está depurando. En caso contrario, este método debe devolver `S_FALSE`.  
  
 Cuando se llama a este método, debe enviar la DE la [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) objeto de evento, si no la ha enviado para esta instancia de la [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interfaz, así como el [ IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) y [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) objetos de evento. El [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) , a continuación, se envía el objeto de evento si el `dwReason` parámetro es `ATTACH_REASON_LAUNCH`.  
  
 Debe llamar la DE la [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) método en el [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto proporcionado por el [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) eventos de objetos y debe almacenar el GUID del programa en los datos de instancia para el `IDebugProgram2` objeto implementado por la DE.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)   
 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
