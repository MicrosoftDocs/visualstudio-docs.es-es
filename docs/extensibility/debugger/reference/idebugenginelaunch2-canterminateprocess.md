---
title: IDebugEngineLaunch2::CanTerminateProcess ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
helpviewer_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
ms.assetid: 7973454d-c957-4123-a0ee-80ebcdbbd2d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 91c68e0a0e314015c1f2e6df2a96243c6ce854e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730560"
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
[en] Un [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) objeto que representa el proceso que se va a terminar.

## <a name="return-value"></a>Valor devuelto
 Si se `S_OK`realiza correctamente, devuelve ; de lo contrario devuelve un código de error. Devuelve `S_FALSE` si el motor no puede finalizar el proceso, por ejemplo, porque se deniega el acceso.

## <a name="remarks"></a>Observaciones
 Si este `S_OK`método devuelve , a continuación, el [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md) método se puede llamar para terminar realmente el proceso.

## <a name="see-also"></a>Vea también
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)
