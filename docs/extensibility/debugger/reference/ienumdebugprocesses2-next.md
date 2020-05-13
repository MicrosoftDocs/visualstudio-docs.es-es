---
title: IEnumDebugProcesses2::Siguiente Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2::Next
helpviewer_keywords:
- IEnumDebugProcesses2::Next
ms.assetid: abef89eb-198b-49cd-a4c9-17bce6cac0e1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cbfab7f13160129249afe7139ef3c402ba9801ee
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715835"
---
# <a name="ienumdebugprocesses2next"></a>IEnumDebugProcesses2::Next
Devuelve el conjunto de elementos siguiente de la enumeración.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Next(
   ULONG            celt,
   IDebugProcess2** rgelt,
   ULONG*           pceltFetched
);
```

```csharp
int Next(
   uint             celt,
   IDebugProcess2[] rgelt,
   ref uint         pceltFetched
);
```

## <a name="parameters"></a>Parámetros
`celt`\
[in] Número de elementos que se van a recuperar. También especifica el tamaño `rgelt` máximo de la matriz.

`rgelt`\
[adentro, fuera] Matriz de [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) elementos que se van a rellenar.

`pceltFetched`\
[fuera] Devuelve el número de `rgelt`elementos devueltos realmente en .

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si se puede devolver menos que el número solicitado de elementos; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
