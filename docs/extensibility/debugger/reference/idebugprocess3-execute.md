---
title: IDebugProcess3::Ejecutar ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 444eadcce38adbd8ecd8655e8e0dc3f36f446848
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723684"
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
Continúa ejecutando este proceso desde un estado detenido. Cualquier estado de ejecución anterior (por ejemplo, un paso) se borra y el proceso comienza a ejecutarse de nuevo.

> [!NOTE]
> Este método debe utilizarse en lugar de [Ejecutar](../../../extensibility/debugger/reference/idebugprogram2-execute.md).

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
[en] Un [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa el subproceso que se va a ejecutar.

## <a name="return-value"></a>Valor devuelto
 Si se `S_OK`realiza correctamente, devuelve ; de lo contrario, devuelve el código de error.

## <a name="remarks"></a>Observaciones
 Cuando el usuario inicia la ejecución desde un estado detenido en el subproceso de algún otro proceso, se llama a este método en este proceso. Este método también se llama cuando el usuario selecciona el **comando Inicio** desde **el** depurar menú en el IDE. La implementación de este método puede ser tan simple como llamar a la [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) método en el subproceso actual en el proceso.

> [!WARNING]
> No envíe un evento de detención o un evento inmediato (sincrónico) a [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) mientras controla esta llamada; de lo contrario, el depurador puede bloquearse.

## <a name="see-also"></a>Vea también
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Reanudación](../../../extensibility/debugger/reference/idebugthread2-resume.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
