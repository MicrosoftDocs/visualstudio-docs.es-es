---
title: IDebugProgram2::Step | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::Step
helpviewer_keywords: IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a7142f79f4406611eb4ab3cbb6695cb2d0305bed
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
Realiza un paso.  
  
> [!NOTE]
>  Este método está en desuso. Use la [paso](../../../extensibility/debugger/reference/idebugprocess3-step.md) método en su lugar.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Step(   
   IDebugThread2*  pThread,  
   STEPKIND        sk,  
   STEPUNIT        step  
);  
```  
  
```csharp  
int Step(   
   IDebugThread2  pThread,  
   enum_STEPKIND  sk,  
   enum_STEPUNIT  step  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pThread`  
 [in] Un [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa el subproceso que se está ejecutando paso.  
  
 `sk`  
 [in] Un valor de la [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) enumeración que especifica el tipo de paso.  
  
 `step`  
 [in] Un valor de la [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) enumeración que especifica la unidad de paso (por ejemplo, mediante la instrucción o instrucciones).  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 En caso de que no hay ninguna sincronización de subprocesos o la comunicación entre subprocesos, otros subprocesos en el programa deben ejecutarse cuando un subproceso determinado está aumentando.  
  
> [!WARNING]
>  No se envía ningún evento de detención o a un evento (sincrónico) inmediato [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) al controlar esta llamada; en caso contrario, el depurador puede dejar de responder.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)