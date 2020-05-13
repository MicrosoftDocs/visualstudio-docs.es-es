---
title: IDebugAlias::Dispose ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::Dispose
helpviewer_keywords:
- IDebugAlias::Dispose method
ms.assetid: e84909a4-d378-4f48-bf25-2c014c77c8e3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: df3a2ecc50063df8f90645b9ccaa72754c3728c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736557"
---
# <a name="idebugaliasdispose"></a>IDebugAlias::Dispose
Marca este alias para su eliminación.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Dispose();
```

```csharp
int Dispose();
```

## <a name="parameters"></a>Parámetros
 Ninguno.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Una vez que se llama a este método, el alias ya no está disponible.

## <a name="see-also"></a>Vea también
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
