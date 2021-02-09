---
title: 'IEnumDebugThreads2:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2::Next
helpviewer_keywords:
- IEnumDebugThreads2::Next
ms.assetid: bcffd954-3c67-4867-96f3-041ddb3e34d4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5c75ec9986ba13dcc287c86e0a57d88e9c769788
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852887"
---
# <a name="ienumdebugthreads2next"></a>IEnumDebugThreads2::Next
Devuelve el conjunto de elementos siguiente de la enumeración.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Next(
   ULONG           celt,
   IDebugThread2** rgelt,
   ULONG*          pceltFetched
);
```

```csharp
int Next(
   uint            celt,
   IDebugThread2[] rgelt,
   ref uint        pceltFetched
);
```

## <a name="parameters"></a>Parámetros
`celt`\
[in] Número de elementos que se van a recuperar. También especifica el tamaño máximo de la `rgelt` matriz.

`rgelt`\
[in, out] Matriz de elementos [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que se va a rellenar.

`pceltFetched`\
enuncia Devuelve el número de elementos realmente devueltos en `rgelt` .

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si se puede devolver menos que el número solicitado de elementos; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
