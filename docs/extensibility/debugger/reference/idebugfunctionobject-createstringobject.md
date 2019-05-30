---
title: IDebugFunctionObject::CreateStringObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateStringObject
helpviewer_keywords:
- IDebugFunctionObject::CreateStringObject method
ms.assetid: fd6070ab-07d4-4ea1-8d71-b16592d6f1a7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 620aef7474f7f669e22fcb44c7df2611dc50bafb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313618"
---
# <a name="idebugfunctionobjectcreatestringobject"></a>IDebugFunctionObject::CreateStringObject
Crea un objeto de cadena.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CreateStringObject( 
   LPCOLESTR      pcstrString,
   IDebugObject** ppObject
);
```

```csharp
int CreateStringObject(
   string      pcstrString,
   out IDebugObject ppOjbect
);
```

## <a name="parameters"></a>Parámetros
`pcstrString`\
[in] El valor de cadena para el objeto de cadena.

`ppObject`\
[out] Devuelve un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto que representa el objeto de cadena recién creado.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Llame a este método para crear un objeto que representa una cadena que es un parámetro a la función representada por el [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfaz.

## <a name="see-also"></a>Vea también
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)