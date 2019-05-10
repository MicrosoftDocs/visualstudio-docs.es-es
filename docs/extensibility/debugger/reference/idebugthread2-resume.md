---
title: IDebugThread2::Resume | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5fc7b8f5cf5cd5360a60e8c6fbf3b6bf43415575
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65225988"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
Reanuda la ejecución de un subproceso.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Resume ( 
   DWORD *pdwSuspendCount
);
```

```csharp
int Resume ( 
   out uint pdwSuspendCount
);
```

## <a name="parameters"></a>Parámetros
 `pdwSuspendCount`\

 [out] Devuelve el recuento de suspensión después de la operación de reanudación.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Cada llamada a este método disminuye el recuento de suspensión hasta que llega a 0 en ese momento, realmente se reanuda la ejecución. Este recuento de suspensión se muestra en el **subprocesos** ventana de depuración.

 Para cada llamada a este método, debe haber una llamada anterior a la [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) método. El recuento de suspensión determina cuántas veces el `IDebugThread2::Suspend` hasta ahora ha llamado al método.

## <a name="see-also"></a>Vea también
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)