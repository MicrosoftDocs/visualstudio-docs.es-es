---
title: IDebugEngineProgram2::Stop | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3cb9627ba11bdec5729383bd6a31e4a338f3ef9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920336"
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
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Este método se llama cuando este programa se está depurando en un entorno de varios programa. Cuando se recibe un evento de detención desde otro programa, este método se llama en este programa. La implementación de este método debe ser asincrónica; es decir, no todos los subprocesos deben detenerse antes de que devuelve este método. La implementación de este método puede ser tan sencilla como llamar a la [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) método en este programa.

 Ningún evento de depuración se envía como respuesta a este método.

## <a name="see-also"></a>Vea también
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)