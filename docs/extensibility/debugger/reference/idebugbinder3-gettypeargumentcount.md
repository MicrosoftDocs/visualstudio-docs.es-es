---
description: Este método devuelve el número de tipos de argumento asociado a este objeto.
title: 'IDebugBinder3:: Gettypeargumentcount (| Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetTypeArgumentCount
helpviewer_keywords:
- IDebugBinder3::GetTypeArgumentCount method
ms.assetid: caf68de6-6f7c-4efd-b803-121347a5032e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aa70a07273a0b4dfdf24219949b411f42b0ddc44
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054496"
---
# <a name="idebugbinder3gettypeargumentcount"></a>IDebugBinder3::GetTypeArgumentCount
Este método devuelve el número de tipos de argumento asociado a este objeto.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetTypeArgumentCount(
   UINT* uCount
);
```

```csharp
int GetTypeArgumentCount(
   out uint uCount
);
```

## <a name="parameters"></a>Parámetros
`uCount`\
enuncia Número de tipos de argumento asociados a este objeto.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 El valor devuelto por este método se puede usar para asignar una matriz para su uso con el método [gettypearguments (](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md) .

## <a name="see-also"></a>Consulte también
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)
