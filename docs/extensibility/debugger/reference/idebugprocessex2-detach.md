---
title: IDebugProcessEx2::Detach ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7379436ae0da57d7f8c47ce8484c810a53a0a453
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723359"
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
Este método informa al proceso de que una sesión ya no está depurando el proceso.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Detach( 
   IDebugSession2* pSession
);
```

```csharp
int Detach(
   IDebugSession2 pSession
);
```

## <a name="parameters"></a>Parámetros
`pSession`\
[en] Valor que identifica de forma única la sesión de la que se va a separar este proceso.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 La interfaz `pSession` pasada debe tratarse solo como una cookie, un valor que identifica de forma única al administrador de depuración de sesión que se adjunta originalmente a este proceso; ninguno de los métodos de la interfaz suministrada son funcionales.

## <a name="see-also"></a>Vea también
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
