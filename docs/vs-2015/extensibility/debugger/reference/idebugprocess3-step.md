---
title: 'IDebugProcess3:: Step | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5069a40f4e3ea4b1fba74c8133a18b46f2b3f2d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "86386230"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Hace que el proceso procese una instrucción o instrucción.  
  
> [!NOTE]
> Este método se debe usar en lugar del [paso](../../../extensibility/debugger/reference/idebugprogram2-step.md).  
  
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
 de Un objeto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa el subproceso escalonado.  
  
 `sk`  
 de Uno de los valores de [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) .  
  
 `step`  
 de Uno de los valores de [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) .  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve el código de error.  
  
## <a name="remarks"></a>Observaciones  
 En caso de que haya cualquier sincronización de subprocesos o comunicación entre subprocesos, otros subprocesos del proceso deben ejecutarse cuando un subproceso determinado se está ejecutando.  
  
 **ADVERTENCIA** de No enviar un evento de detención o un evento inmediato (sincrónico) al [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) mientras se controla esta llamada; de lo contrario, es posible que el depurador deje de responder.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)   
 [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
