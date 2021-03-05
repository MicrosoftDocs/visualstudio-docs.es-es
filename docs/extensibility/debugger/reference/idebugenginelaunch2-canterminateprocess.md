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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 687b2816c6fd312efef29daa44e0644fc5c5c8c6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153630"
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
