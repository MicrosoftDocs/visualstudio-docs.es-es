---
title: 'IDebugArrayObject:: GetElements | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a93e75be0e3a7b3c86e75b29a13b2cabe5a4573
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870173"
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
enuncia Devuelve un objeto [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) que permite enumerar todos los elementos.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
 Como alternativa, use los métodos [getCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) y [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) para recorrer en iteración los elementos.

## <a name="see-also"></a>Vea también
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
