---
description: Obtiene el valor del objeto como una serie consecutiva de bytes.
title: 'IDebugObject:: GetValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 63e07ccfbcf2117363ed3e2096d5f0bb4bcac806
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150450"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
Obtiene el valor del objeto como una serie consecutiva de bytes.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int GetValue(
   ref byte[] pValue,
   uint nSize
);
```

## <a name="parameters"></a>Parámetros
`pValue`\
[in, out] Matriz que se rellena con una serie consecutiva de bytes que representa el valor del objeto.

`nSize`\
de Número máximo de bytes que se van a capturar.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Obtiene el número total de bytes de valor que se pueden capturar llamando al método [Get](../../../extensibility/debugger/reference/idebugobject-getsize.md) .

## <a name="see-also"></a>Consulte también
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
