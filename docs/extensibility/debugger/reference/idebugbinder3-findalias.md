---
title: 'IDebugBinder3:: FindAlias | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1bac818844b69018bb9dc6a970a5659513dbe50d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925089"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Este método busca un alias, dado un nombre. Se buscarán todos los alias del programa.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT FindAlias(
   LPCOLESTR     pcstrName,
   IDebugAlias** ppAlias
);
```

```csharp
int FindAlias(
   string          pcstrName,
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>Parámetros
`pcstrName`\
de Nombre del alias que se va a buscar.

`ppAlias`\
enuncia Alias encontrado (si existe) representado por la interfaz [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) .

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve `S_FALSE` (si no se encuentra el alias) o un código de error.

## <a name="remarks"></a>Notas
 Este método inicializa el objeto de destino en NULL antes de llamar a; después, prueba un valor NULL después para determinar si se encontró o no el alias.

## <a name="see-also"></a>Vea también
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
