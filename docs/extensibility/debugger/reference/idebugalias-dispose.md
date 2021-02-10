---
title: IDebugAlias::D ispose | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::Dispose
helpviewer_keywords:
- IDebugAlias::Dispose method
ms.assetid: e84909a4-d378-4f48-bf25-2c014c77c8e3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 033d74be9548b6bdaaccfe567e99c1d94453bca5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944802"
---
# <a name="idebugaliasdispose"></a>IDebugAlias::Dispose
Marca este alias para su eliminación.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Dispose();
```

```csharp
int Dispose();
```

## <a name="parameters"></a>Parámetros
 Ninguno.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
 Una vez que se llama a este método, el alias deja de estar disponible.

## <a name="see-also"></a>Vea también
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
