---
title: IDebugExceptionEvent2::PassToDebuggee | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cae097b5ce02993fc125aafaffded32a35dde0a5
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56679364"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
Especifica si se debe pasar la excepción el programa que se está depurando cuando se reanuda la ejecución, o si debe descartarse la excepción.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT PassToDebuggee(
   BOOL fPass
);
```

```csharp
int PassToDebuggee(
   int fPass
);
```

#### <a name="parameters"></a>Parámetros
 `fPass`

 [in] Distinto de cero (`TRUE`) si la excepción se debe pasar el programa que se está depurando cuando se reanuda la ejecución, o cero (`FALSE`) si la excepción debe descartarse.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Llamar a este método no hace realmente que cualquier código que se ejecutará en el programa que se está depurando. La llamada consiste simplemente en establecer el estado de la ejecución de código siguiente. Por ejemplo, las llamadas a la [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) método puede devolver `S_OK` con el [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md).`dwState` campo establecido en `EXCEPTION_STOP_SECOND_CHANCE`.

 El IDE puede recibir el [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) evento y llamar a la [continuar](../../../extensibility/debugger/reference/idebugprogram2-continue.md) método. El motor de depuración (DE) debe tener un comportamiento predeterminado para controlar el caso si el `PassToDebuggee` no se llama al método.

## <a name="see-also"></a>Vea también
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)
- [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)