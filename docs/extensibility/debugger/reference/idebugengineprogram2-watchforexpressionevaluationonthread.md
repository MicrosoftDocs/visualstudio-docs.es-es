---
title: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e988e1d64af38a55f5d946f704e1edb4df29b1d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730364"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
Permite (o no permite) que se produzca la evaluación de expresiones en el subproceso dado, incluso si el programa se ha detenido.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT WatchForExpressionEvaluationOnThread( 
   IDebugProgram2*       pOriginatingProgram,
   DWORD                 dwTid,
   DWORD                 dwEvalFlags,
   IDebugEventCallback2* pExprCallback,
   BOOL                  fWatch
);
```

```csharp
int WatchForExpressionEvaluationOnThread( 
   IDebugProgram2       pOriginatingProgram,
   uint                  dwTid,
   uint                  dwEvalFlags,
   IDebugEventCallback2 pExprCallback,
   int                   fWatch
);
```

## <a name="parameters"></a>Parámetros
`pOriginatingProgram`\
[en] Un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa el programa que está evaluando una expresión.

`dwTid`\
[en] Especifica el identificador del subproceso.

`dwEvalFlags`\
[en] Combinación de indicadores de la enumeración [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) que especifican cómo se va a realizar la evaluación.

`pExprCallback`\
[en] Un [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objeto que se usará para enviar eventos de depuración que se producen durante la evaluación de expresiones.

`fWatch`\
[en] Si no es`TRUE`cero ( ), permite `dwTid`la evaluación de expresiones en el subproceso identificado por ; de lo`FALSE`contrario, cero ( ) no permite la evaluación de expresiones en ese subproceso.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Cuando el administrador de depuración de sesión `pOriginatingProgram` (SDM) pide a un programa, identificado por el parámetro, que evalúe una expresión, notifica a todos los demás programas adjuntos llamando a este método.

 La evaluación de expresiones en un programa puede hacer que `IDispatch` el código se ejecute en otro, debido a la evaluación de funciones o la evaluación de cualquier propiedad. Debido a esto, este método permite que la evaluación de expresiones se ejecute y se complete aunque el subproceso se detenga en este programa.

## <a name="see-also"></a>Vea también
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
