---
title: IDebugProcess3::Execute | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 95dc4728c3c51dc8e206393ccb2a8f27f470a51b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
Continúa ejecutando este proceso desde un estado de detención. Cualquier estado de ejecución anterior (por ejemplo, un paso) está desactivada y el proceso empieza a ejecutarse de nuevo.  
  
> [!NOTE]
>  Este método debe utilizarse en lugar de [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Execute(  
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Execute(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pThread`  
 [in] Un [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa el subproceso que ejecute.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve el código de error.  
  
## <a name="remarks"></a>Comentarios  
 Cuando el usuario inicia la ejecución de un estado de detención en el subproceso de otro proceso, se llama a este método en este proceso. También se llama a este método cuando el usuario selecciona el **iniciar** línea de comandos desde el **depurar** menú en el IDE. La implementación de este método puede ser tan sencilla como llamar a la [reanudar](../../../extensibility/debugger/reference/idebugthread2-resume.md) método en el subproceso actual en el proceso.  
  
> [!WARNING]
>  No se envía ningún evento de detención o a un evento (sincrónico) inmediato [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) al controlar esta llamada; en caso contrario, el depurador puede dejar de responder.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Reanudar](../../../extensibility/debugger/reference/idebugthread2-resume.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)