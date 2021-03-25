---
description: Determina si se puede finalizar un proceso.
title: 'IDebugEngineLaunch2:: CanTerminateProcess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
helpviewer_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
ms.assetid: 7973454d-c957-4123-a0ee-80ebcdbbd2d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 20df2c6d44e9bb0afd6610d6ded01ed637035b4b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077452"
---
# <a name="idebugenginelaunch2canterminateprocess"></a>IDebugEngineLaunch2::CanTerminateProcess
Determina si se puede finalizar un proceso.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CanTerminateProcess ( 
   IDebugProcess2* pProcess
);
```

```csharp
int CanTerminateProcess ( 
   IDebugProcess2 pProcess
);
```

## <a name="parameters"></a>Parámetros
`pProcess`\
de Objeto [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) que representa el proceso que se va a terminar.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve un código de error. Devuelve `S_FALSE` si el motor no puede finalizar el proceso, por ejemplo, porque se denegó el acceso.

## <a name="remarks"></a>Observaciones
 Si este método devuelve `S_OK` , se puede llamar al método [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md) para finalizar realmente el proceso.

## <a name="see-also"></a>Consulte también
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)
