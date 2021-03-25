---
description: Recupera un tipo a partir de su tipo primitivo.
title: 'IDebugDynamicFieldCOMPlus:: GetTypeFromPrimitive | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDynamicFieldCOMPlus::GetTypeFromPrimitive
- GetTypeFromPrimitive
ms.assetid: d7f51e2a-1b72-489c-b7b6-4af7b7e4d663
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2b222546f529aca563d6e54a674d7c361111decb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094047"
---
# <a name="idebugdynamicfieldcomplusgettypefromprimitive"></a>IDebugDynamicFieldCOMPlus::GetTypeFromPrimitive
Recupera un tipo a partir de su tipo primitivo.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetTypeFromPrimitive(
   DWORD         dwCorElementType,
   IDebugField** ppType
);
```

```csharp
int GetTypeFromPrimitive(
   uint            dwCorElementType,
   out IDebugField ppType
);
```

## <a name="parameters"></a>Parámetros
`dwCorElementType`\
de Valor de la [enumeración CorElementType](/dotnet/framework/unmanaged-api/metadata/corelementtype-enumeration) que representa el tipo primitivo.

`ppType`\
enuncia Devuelve el [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que representa el tipo.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Consulte también
- [IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)
