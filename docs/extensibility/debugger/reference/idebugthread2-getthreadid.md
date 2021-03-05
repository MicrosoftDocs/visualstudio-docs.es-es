---
description: Obtiene el identificador del subproceso del sistema.
title: 'IDebugThread2:: GetThreadId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetThreadId
helpviewer_keywords:
- IDebugThread2::GetThreadId
ms.assetid: db8b1c07-6b86-47f9-b292-bac19c276d36
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 95dd724310b3aae6e2266d9d18a3846bc9efccf7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164557"
---
# <a name="idebugthread2getthreadid"></a>IDebugThread2::GetThreadId
Obtiene el identificador del subproceso del sistema.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetThreadId (
    DWORD* pdwThreadId
);
```

```csharp
int GetThreadId (
    out uint pdwThreadId
);
```

## <a name="parameters"></a>Parámetros
`pdwThreadId`\
enuncia Devuelve el identificador del subproceso del sistema.

## <a name="return-value"></a>Valor devuelto
Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
Un identificador de subproceso se utiliza para identificar un subproceso entre todos los demás subprocesos de un proceso.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra cómo implementar este método para un `CProgram` objeto simple que implementa la interfaz [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) .

```cpp
HRESULT CProgram::GetThreadId(DWORD* pdwThreadId) {
    *pdwThreadId = GetCurrentThreadId();
    return NOERROR;
}
```

## <a name="see-also"></a>Consulte también
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
