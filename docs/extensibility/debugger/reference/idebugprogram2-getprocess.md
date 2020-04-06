---
title: IDebugProgram2::GetProcess ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aca1842e92e7e1c164a6468e6c1e94a352ef67c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722783"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
Obtenga el proceso en el que se ejecuta este programa.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetProcess(
   IDebugProcess2** ppProcess
);
```

```csharp
int GetProcess(
   out IDebugProcess2 ppProcess
);
```

## <a name="parameters"></a>Parámetros
`ppProcess`\
[fuera] Devuelve el [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) interfaz que representa el proceso.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 A menos que un motor de depuración (DE) implementa el [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) interfaz, la implementación de la DE de este método siempre debe devolver `E_NOTIMPL` porque un DE no puede determinar en qué proceso se está ejecutando y, por lo tanto, no puede satisfacer una implementación de este método.

 Implementar `IDebugEngineLaunch2` la interfaz significa que la DE debe saber cómo crear un proceso; por lo tanto, la implementación de la DE de la [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaz es capaz de saber en qué proceso se está ejecutando.

## <a name="see-also"></a>Vea también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
