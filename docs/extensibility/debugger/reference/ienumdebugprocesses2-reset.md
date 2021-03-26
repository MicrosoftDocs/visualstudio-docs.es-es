---
description: Restablece la enumeración de procesos en el primer elemento.
title: 'IEnumDebugProcesses2:: RESET | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2::Reset
helpviewer_keywords:
- IEnumDebugProcesses2::Reset
ms.assetid: 31cbde4f-0bba-497a-9969-d2c342ef4a7b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 233f6e6226f6469f58c240ff299bd5fb70ca9f40
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091557"
---
# <a name="ienumdebugprocesses2reset"></a>IEnumDebugProcesses2::Reset
Restablece la enumeración al primer elemento.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Reset(
   void
);
```

```csharp
int Reset();
```

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Después de llamar a este método, la siguiente llamada al método [siguiente](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md) devuelve el primer elemento de la enumeración.

## <a name="see-also"></a>Consulte también
- [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)
