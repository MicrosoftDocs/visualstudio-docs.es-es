---
title: 'IEnumDebugCodeContexts2:: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2::Clone
helpviewer_keywords:
- IEnumDebugCodeContexts2::Clone
ms.assetid: 22c98975-4294-4fbd-a345-16f65fe1200d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a877fcda76cca704e12d228cf4e51ab070aa5c3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929516"
---
# <a name="ienumdebugcodecontexts2clone"></a>IEnumDebugCodeContexts2::Clone
Devuelve una copia de la enumeración actual como objeto independiente.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Clone(
   IEnumDebugCodeContexts2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugCodeContexts2 ppEnum
);
```

## <a name="parameters"></a>Parámetros
`ppEnum`\
[out] Devuelve una copia de esta enumeración como un objeto independiente.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
 La copia de la enumeración tiene el mismo estado que el original en el momento en que se llama a este método. Sin embargo, los Estados de la copia y del original son independientes y se pueden cambiar individualmente.

## <a name="see-also"></a>Vea también
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)
