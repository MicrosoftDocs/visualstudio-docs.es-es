---
title: IDebugArrayObject::GetElements | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 915724fa5790c6b8c9fde2706b1222db239cb4ab
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351794"
---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
Obtiene un enumerador de todos los elementos de la matriz.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetElements( 
   IEnumDebugObjects** ppEnum
);
```

```csharp
int GetElements(
   out IEnumDebugObjects ppEnum
);
```

## <a name="parameters"></a>Parámetros
`ppEnum`\
[out] Devuelve un [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) objeto que permite enumerar sobre todos los elementos.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Como alternativa, use el [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) y [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) métodos para recorrer en iteración los elementos.

## <a name="see-also"></a>Vea también
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)