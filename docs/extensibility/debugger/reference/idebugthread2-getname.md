---
title: IDebugThread2::GetName ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9d4828b573585969154f2ad1d484c9fcdf767417
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718771"
---
# <a name="idebugthread2getname"></a>IDebugThread2::GetName
Obtiene el nombre de un subproceso.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetName ( 
   BSTR* pbstrName
);
```

```csharp
int GetName ( 
   out string pbstrName
);
```

## <a name="parameters"></a>Parámetros
`pbstrName`\
[fuera] Devuelve el nombre del subproceso.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 El nombre recuperado siempre es un nombre que se puede mostrar y este nombre describe el subproceso. El nombre del subproceso puede derivarse de una arquitectura en tiempo de ejecución que admite subprocesos con nombre, o puede ser un nombre derivado del motor de depuración. Como alternativa, el nombre del subproceso se puede establecer mediante una llamada a la [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md) método.

## <a name="see-also"></a>Vea también
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)
