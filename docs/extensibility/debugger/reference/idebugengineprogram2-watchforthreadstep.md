---
title: IDebugEngineProgram2::WatchForThreadStep ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cf0474d527b7c6f1d180201a463f52a0b17d18fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730359"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
Busca la ejecución (o deja de observar la ejecución) para que se produzca en el subproceso dado.

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
[en] Un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa el programa que se está escalonando.

`dwTid`\
[en] Especifica el identificador del subproceso que se va a ver.

`fWatch`\
[en] Distinto de`TRUE`cero ( ) significa comenzar a `dwTid`observar la ejecución en el subproceso identificado por ; de lo`FALSE`contrario, cero ( ) `dwTid`significa dejar de mirar para la ejecución en .

`dwFrame`\
[en] Especifica un índice de marco que controla el tipo de paso. Cuando este valor es cero (0), el tipo de paso es "paso `dwTid` a paso" y el programa debe detenerse cada vez que se ejecuta el subproceso identificado por. Cuando `dwFrame` es distinto de cero, el tipo de paso es "paso a `dwTid` paso" y el programa debe detenerse solo `dwFrame`si el subproceso identificado por se está ejecutando en un marco cuyo índice es igual o superior a la pila que .

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Cuando el administrador de depuración de sesión `pOriginatingProgram` (SDM) pasa un programa, identificado por el parámetro, notifica a todos los demás programas adjuntos llamando a este método.

 Este método solo es aplicable al paso del mismo subproceso.

## <a name="see-also"></a>Vea también
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
