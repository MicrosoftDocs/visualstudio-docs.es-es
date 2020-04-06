---
title: IDebugAlias::GetName ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::GetName
helpviewer_keywords:
- IDebugAlias::GetName method
ms.assetid: ac2d8891-56b5-40ef-9866-ed74f18bb043
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a8ebb10e5b01d95b6d9437f41b3ccf2b6c8b99d4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736451"
---
# <a name="idebugaliasgetname"></a>IDebugAlias::GetName
Obtiene el nombre de este alias.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetName(
   BSTR* pbstrName
);
```

```csharp
int GetName(
   out string pbstrName
);
```

## <a name="parameters"></a>Parámetros
`pbstrName`\
[fuera] Nombre del alias.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
