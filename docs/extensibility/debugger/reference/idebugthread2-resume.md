---
description: Reanuda la ejecución de un subproceso.
title: 'IDebugThread2:: resume | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 64a7d5509ac098f6b3a47c3606b6ec530bb6b65b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164505"
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
enuncia Devuelve el recuento de suspensión después de la operación de reanudación.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Cada llamada a este método disminuye el recuento de suspensiones hasta que llega a 0 en el momento en el que se reanuda la ejecución. Este recuento de suspensión se muestra en la ventana de depuración de **subprocesos** .

 Para cada llamada a este método, debe haber una llamada anterior al método [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) . El recuento de suspensión determina cuántas veces se ha llamado al método hasta el `IDebugThread2::Suspend` momento.

## <a name="see-also"></a>Consulte también
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Suspender](../../../extensibility/debugger/reference/idebugthread2-suspend.md)
