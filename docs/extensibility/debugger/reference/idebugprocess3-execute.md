---
title: IDebugProcess3::Execute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b2870a50f4ab8bb0358e2e38529e996b143b7ae
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2019
ms.locfileid: "66202379"
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
Continúa la ejecución de este proceso de un estado detenido. Cualquier estado de ejecución anterior (por ejemplo, un paso) está desactivada y el proceso comienza a ejecutarse de nuevo.

> [!NOTE]
> Este método debería usarse en lugar de [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md).

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

## <a name="parameters"></a>Parámetros
`pThread`\
[in] Un [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa la ejecución del subproceso.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve el código de error.

## <a name="remarks"></a>Comentarios
 Cuando el usuario inicia la ejecución de un estado detenido en el subproceso de algún otro proceso, este método se llama en este proceso. Este método también se llama cuando el usuario selecciona el **iniciar** comando desde el **depurar** menú en el IDE. La implementación de este método puede ser tan sencilla como llamar a la [reanudar](../../../extensibility/debugger/reference/idebugthread2-resume.md) método en el subproceso actual en el proceso.

> [!WARNING]
> No enviar un evento de detención o a un evento (sincrónico) inmediato [eventos](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) mientras se controla esta llamada; en caso contrario, el depurador puede dejar de responder.

## <a name="see-also"></a>Vea también
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)