---
title: IDebugProcess3::Step | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess3::Step
helpviewer_keywords: IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d7bd62bc141e3c5c63a887f683b7e252d466ea83
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
Hace que el proceso paso a paso una instrucción o instrucción.  
  
> [!NOTE]
>  Este método debe utilizarse en lugar de [paso](../../../extensibility/debugger/reference/idebugprogram2-step.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Step(  
   IDebugThread2* pThread,  
   STEPKIND       sk,  
   STEPUNIT       step,  
);  
```  
  
```csharp  
int Step(  
   IDebugThread2 pThread,   
   enum_STEPKIND sk,   
   enum_STEPUNIT step  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pThread`  
 [in] Un [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa el subproceso que se está ejecutando paso.  
  
 `sk`  
 [in] Uno de los [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) valores.  
  
 `step`  
 [in] Uno de los [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) valores.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve el código de error.  
  
## <a name="remarks"></a>Comentarios  
 En caso de que no hay ninguna sincronización de subprocesos o la comunicación entre subprocesos, otros subprocesos del proceso deben ejecutarse cuando un subproceso determinado está aumentando.  
  
 **Advertencia** no se envía ningún evento de detención o a un evento (sincrónico) inmediato [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) al controlar esta llamada; en caso contrario, el depurador puede dejar de responder.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)   
 [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)