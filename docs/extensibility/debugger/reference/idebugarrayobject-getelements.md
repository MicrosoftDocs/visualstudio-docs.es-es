---
title: IDebugArrayObject::GetElements ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: be06acbef93d8858557fea5bd7563168be2d28aa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736236"
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
[fuera] Devuelve un [objeto IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) que permite enumerar todos los elementos.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Como alternativa, use el [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) y [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) métodos para recorrer en iteración los elementos.

## <a name="see-also"></a>Vea también
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
