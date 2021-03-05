---
description: Obtiene el tipo de elemento de la matriz.
title: 'IDebugArrayField:: GetElementType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetElementType
helpviewer_keywords:
- IDebugArrayField::GetElementType method
ms.assetid: c46bf625-0a48-4cbb-8f1f-286356f2c065
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9624a04ae70c8d29abd9b8af5b597b583efb7834
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143849"
---
# <a name="idebugarrayfieldgetelementtype"></a>IDebugArrayField::GetElementType
Obtiene el tipo de elemento de la matriz.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetElementType( 
   IDebugField** ppType
);
```

```csharp
int GetElementType(
   out IDebugField ppType
);
```

## <a name="parameters"></a>Parámetros
`ppType`\
enuncia Devuelve un objeto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que describe el tipo de elemento.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 El objeto [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md) supone que todos los elementos de la matriz son del mismo tipo.

## <a name="see-also"></a>Consulte también
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
