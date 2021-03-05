---
description: Este método informa al proceso de que una sesión está depurando el proceso.
title: 'IDebugProcessEx2:: Attach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Attach
helpviewer_keywords:
- IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1938ae8299612caabe2fe684b7b5c1af685d4596
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149748"
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
de Valor que identifica de forma única la sesión que se adjunta a este proceso.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 La interfaz que se pasa `pSession` se trata únicamente como una cookie, un valor que identifica de forma única el administrador de depuración de la sesión que se asocia a este proceso; ninguno de los métodos de la interfaz proporcionada es funcional.

## <a name="see-also"></a>Consulte también
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
