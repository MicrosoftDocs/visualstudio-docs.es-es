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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c6439200ce0865fe7e6efd2424be0c5798e02dfa
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081365"
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
