---
title: IDebugProgram2::Ejecutar ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f34ebea67ff95d1da6d777cdd828604f4a2f56e8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722985"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
Continúa ejecutando este programa desde un estado detenido. Cualquier estado de ejecución anterior (por ejemplo, un paso) se borra y el programa comienza a ejecutarse de nuevo.

> [!NOTE]
> Este método es desusado. Utilice el método [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md) en su lugar.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Execute(
   void
);
```

```csharp
int Execute();
```

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Cuando el usuario inicia la ejecución desde un estado detenido en el subproceso de algún otro programa, se llama a este método en este programa. Este método también se llama cuando el usuario selecciona el **comando Inicio** desde **el** depurar menú en el IDE. La implementación de este método puede ser tan simple como llamar al método [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) en el subproceso actual del programa.

> [!WARNING]
> No envíe un evento de detención o un evento inmediato (sincrónico) a [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) mientras controla esta llamada; de lo contrario, el depurador puede bloquearse.

## <a name="see-also"></a>Vea también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Reanudación](../../../extensibility/debugger/reference/idebugthread2-resume.md)
