---
description: Obtiene una descripción de las propiedades de un marco de pila.
title: 'IDebugStackFrame2:: Getdebugproperty (| Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetDebugProperty
helpviewer_keywords:
- IDebugStackFrame2::GetDebugProperty
ms.assetid: 02c2fa04-1424-4bca-9936-feaecd2afab6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5c4017e5a14619c2ab5e3f98de65d7d2295e8586
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053482"
---
# <a name="idebugstackframe2getdebugproperty"></a>IDebugStackFrame2::GetDebugProperty
Obtiene una descripción de las propiedades de un marco de pila.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetDebugProperty ( 
   IDebugProperty2** ppDebugProp
);
```

```csharp
int GetDebugProperty ( 
   out IDebugProperty2 ppDebugProp
);
```

## <a name="parameters"></a>Parámetros
`ppDebugProp`\
enuncia Devuelve un objeto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que describe las propiedades de este marco de pila.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 La llamada al método [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) con los filtros adecuados puede recuperar las variables locales, los parámetros de método, los registros y el puntero "this" asociado al marco de pila.

## <a name="see-also"></a>Consulte también
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
