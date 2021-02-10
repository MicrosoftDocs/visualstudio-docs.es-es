---
title: IDebugProcessEx2::D Etach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62ca404442d6bf6080972f03c3e2fd0da2621e20
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954896"
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
de Valor que identifica de forma única la sesión de la que se va a desasociar este proceso.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
 La interfaz que se pasa `pSession` se trata únicamente como una cookie, un valor que identifica de forma única el administrador de depuración de la sesión que se adjuntó originalmente a este proceso; ninguno de los métodos de la interfaz proporcionada es funcional.

## <a name="see-also"></a>Vea también
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
