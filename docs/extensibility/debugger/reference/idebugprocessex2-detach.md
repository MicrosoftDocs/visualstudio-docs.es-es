---
title: IDebugProcessEx2::Detach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e736c14b1a87188f45658a51cff0c123553332e9
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56725039"
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
Este método informa al proceso que una sesión ya no está depurando el proceso.

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

#### <a name="parameters"></a>Parámetros
 `pSession`

 [in] Un valor que identifica de forma única la sesión para desasociar este proceso de.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 La interfaz pasa `pSession` se tratarán solo como una cookie, un valor que identifica el Administrador de sesión de depuración que originalmente asociado a este proceso; ninguno de los métodos en la interfaz proporcionado son funcional.

## <a name="see-also"></a>Vea también
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)