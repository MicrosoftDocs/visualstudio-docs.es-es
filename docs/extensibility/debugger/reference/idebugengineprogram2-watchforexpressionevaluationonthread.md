---
title: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a3f89502beeb1e8165450c7c07f3f55f83dd39e1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
Permite la evaluación de expresiones que se produzca en el subproceso determinado, incluso si el programa se ha detenido (o no permite).  
  
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
  
#### <a name="parameters"></a>Parámetros  
 `pOriginatingProgram`  
 [in] Un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa el programa que está evaluando una expresión.  
  
 `dwTid`  
 [in] Especifica el identificador del subproceso.  
  
 `dwEvalFlags`  
 [in] Una combinación de indicadores de la [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) enumeración que especifican cómo se realiza la evaluación.  
  
 `pExprCallback`  
 [in] Un [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objeto que se usará para enviar eventos de depuración que se producen durante la evaluación de expresiones.  
  
 `fWatch`  
 [in] Si es distinto de cero (`TRUE`), permite la evaluación de expresiones en el subproceso identificado por `dwTid`; en caso contrario, cero (`FALSE`) no permite la evaluación de expresiones en ese subproceso.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Cuando el Administrador de sesión de depuración (SDM) pide un programa, identificado por la `pOriginatingProgram` parámetro, para evaluar una expresión, notifica a todos los demás programas asociados mediante una llamada a este método.  
  
 Evaluación de expresiones en un programa puede causar un código para que se ejecute en otro, debido a la evaluación de función o evaluación de cualquier `IDispatch` propiedades. Por este motivo, este método permite la evaluación de expresiones ejecutar y completar, aunque se puede detener el subproceso en este programa.  
  
## <a name="see-also"></a>Vea también  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)