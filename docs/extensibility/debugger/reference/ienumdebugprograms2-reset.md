---
title: IEnumDebugPrograms2::Reset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2::Reset
helpviewer_keywords:
- IEnumDebugPrograms2::Reset
ms.assetid: b289242b-24ea-4df3-a811-20b0c8a903d6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f2f3f7b96b6176ac4df098993c7126a93a9dc618
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317022"
---
# <a name="ienumdebugprograms2reset"></a>IEnumDebugPrograms2::Reset
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
 Después de llamar a este método, la siguiente llamada a la [siguiente](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md) método devuelve el primer elemento de la enumeración.

## <a name="see-also"></a>Vea también
- [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)