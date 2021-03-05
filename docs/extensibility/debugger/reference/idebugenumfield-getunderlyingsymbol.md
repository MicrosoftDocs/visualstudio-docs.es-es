---
description: Este método devuelve un IDebugField que representa el nombre de la enumeración.
title: 'IDebugEnumField:: GetUnderlyingSymbol | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetUnderlyingSymbol
helpviewer_keywords:
- IDebugEnumField::GetUnderlyingSymbol method
ms.assetid: c3b8a117-6708-4cfd-8ffc-5f007d706bc5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7cf657256be2998d1b1fb0c32d12ab9040b14115
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153292"
---
# <a name="idebugenumfieldgetunderlyingsymbol"></a>IDebugEnumField::GetUnderlyingSymbol
Este método devuelve un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que representa el nombre de la enumeración.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetUnderlyingSymbol(
   IDebugField** ppField
);
```

```csharp
int GetUnderlyingSymbol(
   out IDebugField ppField
);
```

## <a name="parameters"></a>Parámetros
`ppField`\
enuncia Devuelve el [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que describe el nombre de esta enumeración.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 El nombre de la enumeración también contiene el tipo de la enumeración, que está enlazado a una ubicación de memoria mediante el uso de [BIND](../../../extensibility/debugger/reference/idebugbinder-bind.md).

## <a name="see-also"></a>Consulte también
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [Volver](../../../extensibility/debugger/reference/idebugbinder-bind.md)
