---
description: Este método devuelve una copia de la enumeración IDebugObjects actual como un objeto independiente.
title: 'IEnumDebugObjects:: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Clone
helpviewer_keywords:
- IEnumDebugObjects::Clone method
ms.assetid: cb7df109-d29a-4218-b900-6809091459dd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 64d8b862de9f068b41a9fc752855b6affa310298
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083068"
---
# <a name="ienumdebugobjectsclone"></a>IEnumDebugObjects::Clone
Este método devuelve una copia de la enumeración actual como un objeto independiente.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Clone(
   IEnumDebugObjects** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugObjects ppEnum
);
```

## <a name="parameters"></a>Parámetros
`ppEnum`\
[out] Devuelve una copia de esta enumeración como un objeto independiente.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 La copia de la enumeración tiene el mismo estado que el original en el momento en que se llama a este método. Sin embargo, los Estados de la copia y del original son independientes y se pueden cambiar individualmente.

## <a name="see-also"></a>Consulte también
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
