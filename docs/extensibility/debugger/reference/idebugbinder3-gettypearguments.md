---
description: Este método recupera una lista de tipos de argumento asociados a este objeto.
title: 'IDebugBinder3:: Gettypearguments (| Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetTypeArguments
helpviewer_keywords:
- IDebugBinder3::GetTypeArguments method
ms.assetid: fa0c37a7-327f-463e-9a9d-bb3f534584cb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cf360e85f4fdc2d641b00c6cd2252e58fa0d06cb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089009"
---
# <a name="idebugbinder3gettypearguments"></a>IDebugBinder3::GetTypeArguments
Este método recupera una lista de tipos de argumento asociados a este objeto.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetTypeArguments(
   UINT          skip,
   UINT          count,
   IDebugField** ppFields,
   UINT*         pFetched
);
```

```csharp
int GetTypeArguments(
   uint          skip,
   uint          count,
   IDebugField[] ppFields,
   out uint      pFetched
);
```

## <a name="parameters"></a>Parámetros
`skip`\
de Número de campos que se van a omitir antes de obtener los tipos de argumento.

`count`\
de El número de campos de argumento que se van a devolver (también especifica el tamaño de la `ppFields` matriz).

`ppFields`\
[in, out] Una matriz de campos que se rellenarán cuando se devuelva este método.

`pFetched`\
[out] \( opcional) el número de campos de tipo de argumento devueltos realmente.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 El número de tipos de argumento se puede obtener con antelación con [gettypeargumentcount (](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md).

## <a name="see-also"></a>Consulte también
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)
