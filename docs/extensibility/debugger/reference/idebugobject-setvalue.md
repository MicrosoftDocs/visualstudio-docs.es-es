---
title: 'IDebugObject:: SetValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9e4652eb3c77a1871063dfa71b464fb1f7c43f94
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726358"
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
Establece el valor del objeto a partir de una serie consecutiva de bytes.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT SetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int SetValue(
   byte[] pValue,
   uint   nSize
);
```

## <a name="parameters"></a>Parámetros
`pValue`\
de Matriz de bytes que representa el nuevo valor.

`nSize`\
de Tamaño del valor en bytes.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Los valores de la matriz se copian en este objeto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , reemplazando cualquier valor existente. El tamaño del nuevo valor puede ser mayor o menor que el valor existente. `IDebugObject`No puede ser una referencia nula.

## <a name="see-also"></a>Vea también
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
