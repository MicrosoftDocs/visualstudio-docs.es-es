---
description: 'IDebugProgram2:: Execute sigue ejecutando este programa desde un estado detenido. Cualquier estado de ejecución anterior (como un paso) se borra y el programa comienza a ejecutarse de nuevo.'
title: 'IDebugProgram2:: Execute | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 72b59066e8b7125216077dbf4f6ed83adfa0ad2c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146046"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
Sigue ejecutando este programa desde un estado detenido. Cualquier estado de ejecución anterior (como un paso) se borra y el programa comienza a ejecutarse de nuevo.

> [!NOTE]
> Este método es desusado. Use en su lugar el método [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md) .

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
 Cuando el usuario inicia la ejecución desde un estado detenido en otro subproceso del programa, se llama a este método en este programa. También se llama a este método cuando el usuario selecciona el comando **iniciar** en el menú **depurar** del IDE. La implementación de este método puede ser tan simple como llamar al método [resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) en el subproceso actual del programa.

> [!WARNING]
> No enviar un evento de detención o un evento inmediato (sincrónico) al [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) mientras se controla esta llamada; de lo contrario, es posible que el depurador deje de responder.

## <a name="see-also"></a>Consulte también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Reanudar](../../../extensibility/debugger/reference/idebugthread2-resume.md)
