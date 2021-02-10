---
title: 'IDebugObject2:: GetAlias | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetAlias
helpviewer_keywords:
- IDebugObject2::GetAlias method
ms.assetid: aa6824d5-c932-42ba-8713-950e7d1fb42f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2f2fa330b98a37f3946ef19bc2f5641b5b525d88
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953492"
---
# <a name="idebugobject2getalias"></a>IDebugObject2::GetAlias
Obtiene el alias asociado a este objeto, si existe.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetAlias(
   IDebugAlias** ppAlias
);
```

```csharp
int GetAlias(
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>Parámetros
`ppAlias`\
enuncia Devuelve un objeto [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) que representa el alias de este objeto; de lo contrario, devuelve un valor null.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
 Se crea un alias para un objeto con una llamada al método [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) .

## <a name="see-also"></a>Vea también
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
