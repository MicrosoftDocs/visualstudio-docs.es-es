---
title: IEnumDebugThreads2::Reset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2::Reset
helpviewer_keywords:
- IEnumDebugThreads2::Reset
ms.assetid: 88980d9a-c4d6-4de4-a9ab-fb56fa71394a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: be3113c1e8a42b652e1ba55899d75cc547526dc9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350818"
---
# <a name="ienumdebugthreads2reset"></a>IEnumDebugThreads2::Reset
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
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Después de llamar a este método, la siguiente llamada a la [siguiente](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md) método devuelve el primer elemento de la enumeración.

## <a name="see-also"></a>Vea también
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)