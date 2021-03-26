---
description: Obtiene el proceso en el que se ejecuta este programa.
title: 'IDebugProgram2:: GetProcess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d87d863b954a9865ff3960f2f2cdd45ac40ce58
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065403"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
Obtiene el proceso en el que se ejecuta este programa.

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
enuncia Devuelve la interfaz [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) que representa el proceso.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 A menos que un motor de depuración (DE) implemente la interfaz [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) , la implementación de de este método siempre debe devolver `E_NOTIMPL` porque un de no puede determinar en qué proceso se está ejecutando y, por tanto, no puede satisfacer una implementación de este método.

 La implementación de la `IDebugEngineLaunch2` interfaz significa que el de debe saber cómo crear un proceso; por lo tanto, la implementación de de la interfaz [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) es capaz de saber en qué proceso se está ejecutando.

## <a name="see-also"></a>Consulte también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
