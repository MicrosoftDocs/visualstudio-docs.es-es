---
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
ms.openlocfilehash: f7534a05879bdae0a885ae0cbe23d072c30132d0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846808"
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

## <a name="remarks"></a>Notas
 Obtiene el número total de bytes de valor que se pueden capturar llamando al método [Get](../../../extensibility/debugger/reference/idebugobject-getsize.md) .

## <a name="see-also"></a>Vea también
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
