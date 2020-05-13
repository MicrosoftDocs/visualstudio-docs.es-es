---
title: IDebugObject::IsReadOnly ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsReadOnly
helpviewer_keywords:
- IDebugObject::IsReadOnly method
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 19546550f916e9d42adf634b0d85958ce9697d28
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726416"
---
# <a name="idebugobjectisreadonly"></a>IDebugObject::IsReadOnly
Determina si este objeto es de solo lectura.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT IsReadOnly( 
   BOOL* pfIsReadOnly
);
```

```csharp
int IsReadOnly(
   out int pfIsReadOnly
);
```

## <a name="parameters"></a>Parámetros
`pfIsReadOnly`\
[fuera] Devuelve distinto de`TRUE`cero ( ) si este objeto es de solo lectura; de lo contrario, devuelve cero (`FALSE`).

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Un objeto de solo lectura no puede cambiar su valor después de crearlo.

## <a name="see-also"></a>Vea también
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
