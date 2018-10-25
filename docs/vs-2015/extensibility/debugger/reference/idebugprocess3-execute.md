---
title: IDebugProcess3::Execute | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f6a7b5b937c95dbe2f21e5faede5c52f8cd215d4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917224"
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Continúa la ejecución de este proceso de un estado detenido. Cualquier estado de ejecución anterior (por ejemplo, un paso) está desactivada y el proceso comienza a ejecutarse de nuevo.  
  
> [!NOTE]
>  Este método debería usarse en lugar de [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md).  
  
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
 [in] Un [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa la ejecución del subproceso.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve el código de error.  
  
## <a name="remarks"></a>Comentarios  
 Cuando el usuario inicia la ejecución de un estado detenido en el subproceso de algún otro proceso, este método se llama en este proceso. Este método también se llama cuando el usuario selecciona el **iniciar** comando desde el **depurar** menú en el IDE. La implementación de este método puede ser tan sencilla como llamar a la [reanudar](../../../extensibility/debugger/reference/idebugthread2-resume.md) método en el subproceso actual en el proceso.  
  
> [!WARNING]
>  No enviar un evento de detención o a un evento (sincrónico) inmediato [eventos](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) mientras se controla esta llamada; en caso contrario, el depurador puede dejar de responder.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Reanudar](../../../extensibility/debugger/reference/idebugthread2-resume.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)

