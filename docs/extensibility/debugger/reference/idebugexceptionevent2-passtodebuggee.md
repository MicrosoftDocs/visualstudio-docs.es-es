---
description: Especifica si la excepción se debe pasar al programa que se está depurando cuando se reanuda la ejecución o si se debe descartar la excepción.
title: IDebugExceptionEvent2::P assToDebuggee | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7fca977aba3657592088879cdad884f6e6325ffd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152863"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
Especifica si la excepción se debe pasar al programa que se está depurando cuando se reanuda la ejecución o si se debe descartar la excepción.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT PassToDebuggee(
   BOOL fPass
);
```

```csharp
int PassToDebuggee(
   int fPass
);
```

## <a name="parameters"></a>Parámetros
`fPass`\
de Es distinto de cero ( `TRUE` ) si la excepción se debe pasar al programa que se está depurando cuando se reanuda la ejecución, o bien, es cero ( `FALSE` ) si se debe descartar la excepción.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 En realidad, llamar a este método no hace que se ejecute código en el programa que se está depurando. La llamada es simplemente para establecer el estado de la siguiente ejecución de código. Por ejemplo, las llamadas al método [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) pueden devolver `S_OK` con el [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md).`dwState` campo establecido en `EXCEPTION_STOP_SECOND_CHANCE` .

 El IDE puede recibir el evento [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) y llamar al método [continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md) . El motor DE depuración (DE) debe tener un comportamiento predeterminado para controlar el caso si `PassToDebuggee` no se llama al método.

## <a name="see-also"></a>Consulte también
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)
- [Continuar](../../../extensibility/debugger/reference/idebugprogram2-continue.md)
