---
title: IEnumDebugProcesses2::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2::Next
helpviewer_keywords:
- IEnumDebugProcesses2::Next
ms.assetid: abef89eb-198b-49cd-a4c9-17bce6cac0e1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0a35ad62d518bf9f19655809a8c1ac924da92bb8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62866252"
---
# <a name="ienumdebugprocesses2next"></a>IEnumDebugProcesses2::Next
Devuelve el siguiente conjunto de elementos de la enumeración.

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

#### <a name="parameters"></a>Parámetros
 `celt`

 [in] El número de elementos que se va a recuperar. También especifica el tamaño máximo de la `rgelt` matriz.

 `rgelt`

 [in, out] Matriz de [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) elementos que deben rellenarse.

 `pceltFetched`

 [out] Devuelve el número de elementos realmente devueltos en `rgelt`.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si podrían devolverse un menor que el número solicitado de elementos; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)