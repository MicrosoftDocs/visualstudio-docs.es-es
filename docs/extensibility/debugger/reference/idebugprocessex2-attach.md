---
title: IDebugProcessEx2::Attach ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Attach
helpviewer_keywords:
- IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d70da2530a1677367a22968436a17eba809fd24a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723386"
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
Este método informa al proceso de que una sesión está depurando el proceso.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Attach( 
   IDebugSession2* pSession
);
```

```csharp
int Attach(
   IDebugSession2 pSession
);
```

## <a name="parameters"></a>Parámetros
`pSession`\
[en] Valor que identifica de forma única la sesión asociada a este proceso.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 La interfaz `pSession` que se pasa debe tratarse solo como una cookie, un valor que identifica de forma única al administrador de depuración de sesión que se adjunta a este proceso; ninguno de los métodos de la interfaz suministrada son funcionales.

## <a name="see-also"></a>Vea también
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
