---
title: 'IDebugProgramNode2:: Attach_V7 | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842438"
---
# <a name="idebugprogramnode2attach_v7"></a>IDebugProgramNode2::Attach_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

En desuso. NO USE.  
  
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
 de La interfaz [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que representa el programa al que se va a adjuntar.  
  
 `pCallback`  
 de La interfaz [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) que se va a usar para enviar eventos de depuración al SDM.  
  
 `dwReason`  
 de Un valor de la enumeración [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) que especifica el motivo de la asociación.  
  
## <a name="return-value"></a>Valor devuelto  
 Una implementación siempre debe devolver `E_NOTIMPL` .  
  
## <a name="remarks"></a>Notas  
  
> [!WARNING]
> A partir de [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] , este método ya no se utiliza y siempre debe devolver `E_NOTIMPL` . Vea la interfaz [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) para obtener un enfoque alternativo si el nodo del programa debe indicar que no se puede adjuntar o si el nodo del programa simplemente está estableciendo el programa `GUID` . De lo contrario, implemente el método [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) .  
  
## <a name="prior-to-visual-studio-2005"></a>Antes de Visual Studio 2005  
 Este método debe implementarse solo si el DE se ejecuta en el espacio de direcciones del programa que se está depurando. De lo contrario, este método debe devolver `S_FALSE` .  
  
 Cuando se llama a este método, la DE debe enviar el objeto DE evento [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) , si aún no se ha enviado para esta instancia de la interfaz [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) , así como los objetos de evento [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) y [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) . A continuación, se envía el objeto de evento [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) si el `dwReason` parámetro es `ATTACH_REASON_LAUNCH` .  
  
 El parámetro DE debe llamar al método [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) en el objeto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) proporcionado por el objeto de evento [IDEBUGPROGRAMCREATEEVENT2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) y debe almacenar el GUID de ese programa en los datos de instancia para el `IDebugProgram2` objeto implementado por el parámetro de.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Incluir](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)   
 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
