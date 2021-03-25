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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d957743a725ad462a9ed95fca6ebdffbecb6de16
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054132"
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
