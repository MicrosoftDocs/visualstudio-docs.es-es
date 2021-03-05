---
description: Suspende un subproceso.
title: 'IDebugThread2:: Suspend | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0f80799961ccce4b3492b46801b1917055742666
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164453"
---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
Suspende un subproceso.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Suspend ( 
   DWORD *pdwSuspendCount
);
```

```csharp
HRESULT Suspend ( 
   out uint pdwSuspendCount
);
```

## <a name="parameters"></a>Parámetros
`pdwSuspendCount`\
enuncia Devuelve el recuento de suspensión después de la operación de suspensión.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Cada llamada a este método incrementa el recuento de suspensiones por encima de 0. Este recuento de suspensión se muestra en la ventana de depuración de **subprocesos** .

 Para cada llamada a este método, debe haber una llamada posterior al método [resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) .

## <a name="see-also"></a>Consulte también
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Reanudar](../../../extensibility/debugger/reference/idebugthread2-resume.md)
