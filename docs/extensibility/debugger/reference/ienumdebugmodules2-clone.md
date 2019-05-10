---
title: IEnumDebugModules2::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2::Clone
helpviewer_keywords:
- IEnumDebugModules2::Clone
ms.assetid: fd6d3abc-20d9-4f6f-9c8e-5bd29f68d47d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a56330eb2992e517fd76fff12b6a35351c080ef1
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65226720"
---
# <a name="ienumdebugmodules2clone"></a>IEnumDebugModules2::Clone
Devuelve una copia de la enumeración actual como un objeto independiente.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Clone(
   IEnumDebugModules2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugModules2 ppEnum
);
```

## <a name="parameters"></a>Parámetros
 `ppEnum`\

 [out] Devuelve una copia de esta enumeración como un objeto independiente.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 La copia de la enumeración tiene el mismo estado que el original en el momento en que se llama a este método. Sin embargo, los Estados de la copia y el original son independientes y se pueden cambiar de forma individual.

## <a name="see-also"></a>Vea también
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)