---
description: Recupera información sobre si el módulo representa o no el código de usuario.
title: 'IDebugModule3:: IsUserCode | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::IsUserCode
helpviewer_keywords:
- IDebugModule3::IsUserCode
ms.assetid: 77022946-bb8b-4114-aa81-614df6e54b13
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a936d4408b2d289477a860ffca3d53ca7b0ad61d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164843"
---
# <a name="idebugmodule3isusercode"></a>IDebugModule3::IsUserCode
Recupera información sobre si el módulo representa o no el código de usuario.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT IsUserCode(
   BOOL* pfUser
);
```

```csharp
int IsUserCode(
   out int pfUser
);
```

## <a name="parameters"></a>Parámetros
`pfUser`\
enuncia Distinto de cero ( `TRUE` ) si el módulo representa el código de usuario, cero ( `FALSE` ) si no lo hace.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve el código de error.

## <a name="see-also"></a>Consulte también
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
