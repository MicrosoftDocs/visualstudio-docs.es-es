---
title: 'IDebugProcess3:: Execute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f9b70deabd4cb7996d76373c6216057678c0bd3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "86386178"
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Sigue ejecutando este proceso desde un estado detenido. Cualquier estado de ejecución anterior (como un paso) se borra y el proceso empieza a ejecutarse de nuevo.  
  
> [!NOTE]
> Este método se debe usar en lugar de [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Execute(  
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Execute(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pThread`  
 de Objeto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa el subproceso que se va a ejecutar.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve el código de error.  
  
## <a name="remarks"></a>Observaciones  
 Cuando el usuario inicia la ejecución desde un estado detenido en otro subproceso del proceso, se llama a este método en este proceso. También se llama a este método cuando el usuario selecciona el comando **iniciar** en el menú **depurar** del IDE. La implementación de este método puede ser tan simple como llamar al método [resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) en el subproceso actual del proceso.  
  
> [!WARNING]
> No enviar un evento de detención o un evento inmediato (sincrónico) al [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) mientras se controla esta llamada; de lo contrario, es posible que el depurador deje de responder.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Recuper](../../../extensibility/debugger/reference/idebugthread2-resume.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
