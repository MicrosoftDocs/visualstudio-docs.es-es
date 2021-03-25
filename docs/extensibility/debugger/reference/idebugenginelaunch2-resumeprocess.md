---
description: Reanuda la ejecución del proceso.
title: 'IDebugEngineLaunch2:: ResumeProcess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::ResumeProcess
helpviewer_keywords:
- IDebugEngineLaunch2::ResumeProcess
ms.assetid: 61ccc14e-75c6-44e7-aae4-57a9aac52089
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 05c53be36884f60585025cf73da8301b9e51df14
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065975"
---
# <a name="idebugenginelaunch2resumeprocess"></a>IDebugEngineLaunch2::ResumeProcess
Reanuda la ejecución del proceso.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT ResumeProcess ( 
   IDebugProcess2* pProcess
);
```

```csharp
int ResumeProcess ( 
   IDebugProcess2 pProcess
);
```

## <a name="parameters"></a>Parámetros
`pProcess`\
de Objeto [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) que representa el proceso que se va a reanudar.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Se llama a este método una vez que se ha iniciado un proceso con una llamada al método [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) .

## <a name="see-also"></a>Consulte también
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
