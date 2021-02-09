---
title: 'IDebugProgram2:: Continue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 07e48a59f044f8f3ccc94576210a51e7d70d9b66
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912941"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
Sigue ejecutando este programa desde un estado detenido. Cualquier estado de ejecución anterior (como un paso) se conserva y el programa comienza a ejecutarse de nuevo.

> [!NOTE]
> Este método es desusado. En su lugar, use el método [continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) .

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Continue( 
   IDebugThread2* pThread
);
```

```csharp
int Continue( 
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Parámetros
`pThread` de Objeto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa el subproceso.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
 Se llama a este método en este programa independientemente del número de programas que se están depurando o del programa que generó el evento de detención. La implementación debe conservar el estado de ejecución anterior (por ejemplo, un paso) y continuar con la ejecución como si nunca se hubiera detenido antes de completar su ejecución anterior. Es decir, si un subproceso de este programa estaba realizando una operación de paso a paso y se detuvo porque se detuvo algún otro programa y, a continuación, se llamó a este método, el programa debe completar la operación de paso a través original.

> [!WARNING]
> No enviar un evento de detención o un evento inmediato (sincrónico) al [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) mientras se controla esta llamada; de lo contrario, es posible que el depurador deje de responder.

## <a name="see-also"></a>Vea también
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
