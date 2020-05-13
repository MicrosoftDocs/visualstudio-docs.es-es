---
title: IDebugObject::IsNullReference ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e4b6e5f2d28d27deb5e4e1ff8278a071ff9110fd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726520"
---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
Comprueba si este objeto es una referencia nula.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT IsNullReference( 
   BOOL* pfIsNull
);
```

```csharp
int IsNullReference(
   out int pfIsNull
);
```

## <a name="parameters"></a>Parámetros
`pfIsNull`\
[fuera] Devuelve distinto de`TRUE`cero ( ) si este objeto es una referencia nula; de lo contrario, devuelve cero (`FALSE`).

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Una referencia nula significa un objeto vacío o un objeto al que no se ha asignado.

## <a name="see-also"></a>Vea también
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
