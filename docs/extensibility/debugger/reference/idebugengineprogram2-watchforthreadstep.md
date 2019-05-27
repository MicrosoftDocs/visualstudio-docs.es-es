---
title: IDebugEngineProgram2::WatchForThreadStep | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4ed71649a98f86c2d75695ad02cc2aca2ea31a7b
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212434"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
Supervisa la ejecución (o se detiene la ejecución inspeccionando) que se produzca en el subproceso especificado.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT WatchForThreadStep( 
   IDebugProgram2* pOriginatingProgram,
   DWORD           dwTid,
   BOOL            fWatch,
   DWORD           dwFrame
);
```

```csharp
int WatchForThreadStep( 
   IDebugProgram2 pOriginatingProgram,
   uint           dwTid,
   int            fWatch,
   uint           dwFrame
);
```

## <a name="parameters"></a>Parámetros
`pOriginatingProgram`\
[in] Un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa el programa que se va a escalonado.

`dwTid`\
[in] Especifica el identificador del subproceso que se va a inspeccionar.

`fWatch`\
[in] Distinto de cero (`TRUE`) significa que empiece a mirar para su ejecución en el subproceso identificado por `dwTid`; en caso contrario, cero (`FALSE`) significa Detener ejecución inspeccionando en `dwTid`.

`dwFrame`\
[in] Especifica un índice de fotograma que controla el tipo de paso. Cuando se trata de valor es cero (0), el tipo de paso es "step into" y debe detener el programa cada vez que el subproceso identificado por `dwTid` ejecuta. Cuando `dwFrame` es distinto de cero, el tipo de paso es "saltar" y debe detener el programa sólo si el subproceso identificado por `dwTid` se está ejecutando en un marco cuyo índice es igual o superior en la pila que `dwFrame`.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Cuando el Administrador de depuración de la sesión (SDM) los pasos de un programa, identificado por el `pOriginatingProgram` parámetro, notifica a todos los demás programas asociados mediante una llamada a este método.

 Este método solo es aplicable a ejecución paso a paso en el mismo subproceso.

## <a name="see-also"></a>Vea también
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)