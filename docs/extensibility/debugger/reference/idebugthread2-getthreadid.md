---
title: IDebugThread2::GetThreadId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugThread2::GetThreadId
helpviewer_keywords:
- IDebugThread2::GetThreadId
ms.assetid: db8b1c07-6b86-47f9-b292-bac19c276d36
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c77e2d5de5105b964beea0ad880358b59e10fab7
ms.sourcegitcommit: 845442e2b515c3ca1e4e47b46cc1cef4df4f08d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2019
ms.locfileid: "56450119"
---
# <a name="idebugthread2getthreadid"></a>IDebugThread2::GetThreadId
Obtiene el identificador de subproceso del sistema.

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

#### <a name="parameters"></a>Parámetros
`pdwThreadId` [out] Devuelve el identificador de subproceso del sistema.

## <a name="return-value"></a>Valor devuelto
Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
Un identificador de subproceso se usa para identificar un subproceso entre todos los demás subprocesos en un proceso.

## <a name="example"></a>Ejemplo
El ejemplo siguiente muestra cómo implementar este método para una sencilla `CProgram` objeto que implementa el [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) interfaz.

```cpp
HRESULT CProgram::GetThreadId(DWORD* pdwThreadId) {
    *pdwThreadId = GetCurrentThreadId();
    return NOERROR;
}
```

## <a name="see-also"></a>Vea también
[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
