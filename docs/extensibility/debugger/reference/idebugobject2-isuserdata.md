---
title: IDebugObject2::IsUserData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsUserData
helpviewer_keywords:
- IDebugObject2::IsUserData method
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 94c3f6adc9dd75e1ed4ecc4c5fd7f37635099566
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317241"
---
# <a name="idebugobject2isuserdata"></a>IDebugObject2::IsUserData
Determina si el objeto representa datos de usuario.

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
[out] Devuelve cero (`TRUE`) si el objeto representa los datos del usuario; cero (`FALSE`) si no es así.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Datos de usuario están cualquier objeto que forma parte de un módulo que se designa como JustMyCode (una opción configurable por el usuario que marca un módulo como código de usuario y, por tanto, visible en un seguimiento de pila).

## <a name="see-also"></a>Vea también
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)