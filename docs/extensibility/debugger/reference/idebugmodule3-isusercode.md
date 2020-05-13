---
title: IDebugModule3::IsUserCode ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::IsUserCode
helpviewer_keywords:
- IDebugModule3::IsUserCode
ms.assetid: 77022946-bb8b-4114-aa81-614df6e54b13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 435ec50ef5437e5aca5d3722a2041115882d15f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726828"
---
# <a name="idebugmodule3isusercode"></a>IDebugModule3::IsUserCode
Recupera información sobre si el módulo representa el código de usuario o no.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT IsUserCode(
   BOOL* pfUser
);
```

```csharp
int IsUserCode(
   out int pfUser
);
```

## <a name="parameters"></a>Parámetros
`pfUser`\
[fuera] Distinto de`TRUE`cero ( ) si module`FALSE`representa el código de usuario, cero ( ) si no lo hace.

## <a name="return-value"></a>Valor devuelto
 Si se `S_OK`realiza correctamente, devuelve ; de lo contrario, devuelve el código de error.

## <a name="see-also"></a>Vea también
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
