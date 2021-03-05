---
description: Recupera una interfaz de código administrado que representa el valor asociado a este alias.
title: 'IDebugAlias:: GetICorDebugValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b809e16fefb9306da842f39d93bdb3dd0f7b404f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143940"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
Recupera una interfaz de código administrado que representa el valor asociado a este alias.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetICorDebugValue(
   IUnknown** ppUnk
);
```

```csharp
int GetICorDebugValue(
   out object ppUnk
);
```

## <a name="parameters"></a>Parámetros
`ppUnk`\
[out] `IUnknown` interfaz que representa el valor asociado a este alias. Esta interfaz se puede consultar para la `ICorDebugValue` interfaz.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Este método solo se aplica a los valores administrados ( `ICorDebugValue` es una interfaz disponible en el .NET Framework y se define en el SDK de .NET Framework en el archivo Cordebug. idl).

## <a name="see-also"></a>Consulte también
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
