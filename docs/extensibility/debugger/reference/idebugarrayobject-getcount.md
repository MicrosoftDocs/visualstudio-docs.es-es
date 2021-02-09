---
title: 'IDebugArrayObject:: GetCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9750b2982ad0b2d70375fe0519a9fd888bcac8a8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870225"
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

## <a name="remarks"></a>Notas
 Este método ve todos los elementos de un objeto de matriz como una matriz unidimensional, incluso si el objeto de matriz es multidimensional. Por ejemplo, dada la matriz `myarray[3][2][6]` , este método devolvería 36 en el `pdwElements` parámetro. Use el método [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) para recuperar los elementos individuales de uno en uno.

## <a name="see-also"></a>Vea también
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
