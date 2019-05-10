---
title: IEnumDebugPorts2::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2::Next
helpviewer_keywords:
- IEnumDebugPorts2::Next
ms.assetid: 3f43d18c-6bd1-4ddd-95ef-9550abd2ad09
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4c4dace8d337b70a548aa67564fd2d027b88ffc9
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65225486"
---
# <a name="ienumdebugports2next"></a>IEnumDebugPorts2::Next
Devuelve el siguiente conjunto de elementos de la enumeración.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Next(
   ULONG         celt,
   IDebugPort2** rgelt,
   ULONG*        pceltFetched
);
```

```csharp
int Next(
   uint          celt,
   IDebugPort2[] rgelt,
   ref uint      pceltFetched
);
```

## <a name="parameters"></a>Parámetros
 `celt`\

 [in] El número de elementos que se va a recuperar. También especifica el tamaño máximo de la `rgelt` matriz.

 `rgelt`\

 [in, out] Matriz de [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) elementos que deben rellenarse.

 `pceltFetched`\

 [out] Devuelve el número de elementos realmente devueltos en `rgelt`.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si podrían devolverse un menor que el número solicitado de elementos; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)