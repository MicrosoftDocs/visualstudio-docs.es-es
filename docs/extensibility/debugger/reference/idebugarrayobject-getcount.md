---
description: Obtiene el recuento de elementos de la matriz.
title: 'IDebugArrayObject:: GetCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c3a5d052fcb2c40f9dad76791aa992dbfbde72b0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058903"
---
# <a name="idebugarrayobjectgetcount"></a>IDebugArrayObject::GetCount
Obtiene el recuento de elementos de la matriz.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetCount( 
   DWORD* pdwElements
);
```

```csharp
int GetCount(
   out uint pdwElements
);
```

## <a name="parameters"></a>Parámetros
`pdwElements`\
enuncia Devuelve el recuento.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Este método ve todos los elementos de un objeto de matriz como una matriz unidimensional, incluso si el objeto de matriz es multidimensional. Por ejemplo, dada la matriz `myarray[3][2][6]` , este método devolvería 36 en el `pdwElements` parámetro. Use el método [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) para recuperar los elementos individuales de uno en uno.

## <a name="see-also"></a>Consulte también
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
