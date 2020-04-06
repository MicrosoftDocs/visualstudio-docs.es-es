---
title: EVENTATTRIBUTES ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVENTATTRIBUTES
helpviewer_keywords:
- EVENTATTRIBUTES enumeration
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c479058a5e6abb61fb419425706d2a8b26858d04
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737061"
---
# <a name="eventattributes"></a>EVENTATTRIBUTES
Especifica los atributos del evento.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_EVENTATTRIBUTES {
    EVENT_ASYNCHRONOUS          = 0x0000,
    EVENT_SYNCHRONOUS           = 0x0001,
    EVENT_STOPPING              = 0x0002,
    EVENT_ASYNC_STOP            = 0x0002,
    EVENT_SYNC_STOP             = 0x0003,
    EVENT_IMMEDIATE             = 0x0004,
    EVENT_EXPRESSION_EVALUATION = 0x0008
};
typedef DWORD EVENTATTRIBUTES;
```

```csharp
public enum enum_EVENTATTRIBUTES {
    EVENT_ASYNCHRONOUS          = 0x0000,
    EVENT_SYNCHRONOUS           = 0x0001,
    EVENT_STOPPING              = 0x0002,
    EVENT_ASYNC_STOP            = 0x0002,
    EVENT_SYNC_STOP             = 0x0003,
    EVENT_IMMEDIATE             = 0x0004,
    EVENT_EXPRESSION_EVALUATION = 0x0008
};
```

## <a name="fields"></a>Fields
`EVENT_ASYNCHRONOUS`\
Indica que el evento es asincrónico y que no se necesita respuesta al evento.

`EVENT_SYNCHRONOUS`\
Indica que el evento es sincrónico; responder mediante [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md).

`EVENT_STOPPING`\
Indica que se trata de un evento de detención. Debe combinarse `EVENT_ASYNCHRONOUS` con `EVENT_SYNCHRONOUS`cualquiera o .

`EVENT_ASYNC_STOP`\
Indica un evento de detención asincrónico. Actualmente no existe tal evento. Esta marca es solo un marcador de posición.

`EVENT_SYNC_STOP`\
Indica un evento de detención `EVENT_SYNCHRONOUS` sincrónico (una combinación de y `EVENT_STOPPING`). Este valor lo utiliza un motor de depuración (DE) cuando envía un evento de detención. La respuesta se realiza mediante una llamada a [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md), [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)o [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md).

`EVENT_IMMEDIATE`\
Indica un evento que se envía inmediatamente y sincrónicamente al IDE. Esta marca se combina `EVENT_ASYNCHRONOUS`con `EVENT_SYNCHRONOUS`otras `EVENT_SYNC_STOP` marcas como , , o para indicar el tipo de evento y el hecho de que se conoce el mecanismo de respuesta (si existe).

`EVENT_EXPRESSION_EVALUATION`\
El evento es el resultado de la evaluación de expresiones.

## <a name="remarks"></a>Observaciones
Estos valores se `dwAttrib` pasan en el parámetro de la [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) método.

Estos valores se pueden combinar `OR`con un archivo .

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
