---
title: IDebugArrayObject::GetElement | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac59a14a2d3be06c9e1523bcdc0d0ad026e0a7d1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62423691"
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

#### <a name="parameters"></a>Parámetros
 `dwIndex`

 [in] El índice del elemento.

 `ppElement`

 [out] Devuelve un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaz que representa el elemento.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Este método considera todos los elementos de un objeto de matriz como una matriz unidimensional, incluso si el objeto de matriz es multidimensional. Por ejemplo, dada la matriz `myarray[3][2][6]` y un `dwIndex` parámetro de 20, este método devolverá el elemento de `myarray[1][1][2]`y un `dwIndex` devolverá el elemento de parámetro de 21 `myarray[1][1][3]`. Use la [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) método para determinar el número total de elementos de la matriz.

## <a name="see-also"></a>Vea también
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)