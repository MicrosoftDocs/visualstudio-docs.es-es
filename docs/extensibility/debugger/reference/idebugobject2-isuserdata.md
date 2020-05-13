---
title: IDebugObject2::IsUserData ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsUserData
helpviewer_keywords:
- IDebugObject2::IsUserData method
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ce4a7035ac3786f0cc1644e2ebbb0c142167e2b0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726094"
---
# <a name="idebugobject2isuserdata"></a>IDebugObject2::IsUserData
Determina si el objeto representa los datos de usuario.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT IsUserData(
   BOOL* pfUser
);
```

```csharp
int IsUserData(
   out int pfUser
);
```

## <a name="parameters"></a>Parámetros
`pfUser`\
[fuera] Devuelve distinto`TRUE`de cero ( ) si el objeto representa datos de usuario; cero`FALSE`( ) si no lo hace.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Los datos de usuario son cualquier objeto que forma parte de un módulo designado como JustMyCode (una opción configurable por el usuario que marca un módulo como código de usuario y, por lo tanto, visible en un seguimiento de pila).

## <a name="see-also"></a>Vea también
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
