---
title: IDebugBinder3::FindAlias ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0a697e39d21b1c25a98c09ad6cc4837cca7a293
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735865"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Este método localiza un alias, dado un nombre. Esto buscará todos los alias en el programa.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT FindAlias(
   LPCOLESTR     pcstrName,
   IDebugAlias** ppAlias
);
```

```csharp
int FindAlias(
   string          pcstrName,
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>Parámetros
`pcstrName`\
[en] Nombre del alias que se debe buscar.

`ppAlias`\
[fuera] Alias encontrado (si existe) representado por el [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) interfaz.

## <a name="return-value"></a>Valor devuelto
 Si se `S_OK`realiza correctamente, devuelve ; de lo `S_FALSE` contrario, devuelve (si no se encuentra alias) o un código de error.

## <a name="remarks"></a>Observaciones
 Este método inicializa el objeto de destino en null antes de llamar; a continuación, comprueba un valor nulo después para determinar si se encontró o no el alias.

## <a name="see-also"></a>Vea también
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
