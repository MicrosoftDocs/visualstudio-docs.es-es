---
description: Este método obtiene el tipo de campo de clase que representa un nombre de clase completo.
title: 'IDebugSymbolProvider:: GetClassTypeByName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetClassTypeByName
helpviewer_keywords:
- IDebugSymbolProvider::GetClassTypeByName method
ms.assetid: 2c748909-51dc-49b7-b193-19f96fca1138
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 58b7002abf622992dacde4797f41a272177c280e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159671"
---
# <a name="idebugsymbolprovidergetclasstypebyname"></a>IDebugSymbolProvider::GetClassTypeByName
Este método obtiene el tipo de campo de clase que representa un nombre de clase completo.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetClassTypeByName( 
   LPCOLESTR          pszClassName,
   NAME_MATCH         nameMatch,
   IDebugClassField** ppField
);
```

```csharp
int GetClassTypeByName(
   string               pszClassName,
   NAME_MATCH           nameMatch,
   out IDebugClassField ppField
);
```

## <a name="parameters"></a>Parámetros
`pszClassName`\
de Nombre de la clase.

`nameMatch`\
de Selecciona el tipo de coincidencia; por ejemplo, distingue mayúsculas de minúsculas. Un valor de la enumeración [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) .

`ppField`\
enuncia Devuelve el tipo de clase tal y como se representa en la interfaz [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) .

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Consulte también
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
