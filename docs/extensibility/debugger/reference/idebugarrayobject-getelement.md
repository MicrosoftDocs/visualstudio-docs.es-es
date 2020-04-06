---
title: IDebugArrayObject::GetElement ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e29fe09905119057224b45b455e4f56e5ce904af
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736173"
---
# <a name="idebugarrayobjectgetelement"></a>IDebugArrayObject::GetElement
Obtiene un elemento de la matriz.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetElement( 
   DWORD          dwIndex,
   IDebugObject** ppElement
);
```

```csharp
int GetElement(
   [In] uint dwIndex,
   out IDebugObject ppElement
);
```

## <a name="parameters"></a>Parámetros
`dwIndex`\
[en] El índice de elementos.

`ppElement`\
[fuera] Devuelve un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaz que representa el elemento.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Este método ve todos los elementos de un objeto de matriz como una matriz unidimensional, incluso si el objeto de matriz es multidimensional. Por ejemplo, dada `myarray[3][2][6]` la `dwIndex` matriz y un parámetro de 20, este método devolvería el elemento de `myarray[1][1][2]`, y un `dwIndex` parámetro de 21 devolvería el elemento de `myarray[1][1][3]`. Utilice el método [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) para determinar el número total de elementos de la matriz.

## <a name="see-also"></a>Vea también
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
