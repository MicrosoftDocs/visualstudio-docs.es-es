---
title: IDebugBinder3::FindAlias | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8387a3302395d6e25c2b00dd360286e533531168
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344420"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Este método busca un alias, dado un nombre. Realiza una búsqueda en todos los alias en el programa.

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
[in] Nombre de alias para buscar.

`ppAlias`\
[out] Alias que se encuentre (si existe) representado por la [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) interfaz.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` (si no se encuentra el alias) o un código de error.

## <a name="remarks"></a>Comentarios
 Este método inicializa el objeto de destino a null antes de llamar a; después, comprueba un valor null después para determinar si no se encontró el alias.

## <a name="see-also"></a>Vea también
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)