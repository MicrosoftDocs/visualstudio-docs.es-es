---
description: Detiene todos los subprocesos que se ejecutan en este programa.
title: 'IDebugEngineProgram2:: Stop | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7263756a0a8bacbbc6f90e327916cec8868d8f5c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077374"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
Detiene todos los subprocesos que se ejecutan en este programa.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Stop( 
   void 
);
```

```csharp
int Stop();
```

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Se llama a este método cuando este programa se está depurando en un entorno de varios programas. Cuando se recibe un evento de detención de algún otro programa, se llama a este método en este programa. La implementación de este método debe ser asincrónica; es decir, no es necesario detener todos los subprocesos antes de que este método devuelva. La implementación de este método puede ser tan simple como llamar al método [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) en este programa.

 Los implementadores deben enviar un [IDebugStopCompleteEvent2](../../../extensibility/debugger/reference/idebugstopcompleteevent2.md) cuando el programa se detenga.

## <a name="see-also"></a>Consulte también
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
