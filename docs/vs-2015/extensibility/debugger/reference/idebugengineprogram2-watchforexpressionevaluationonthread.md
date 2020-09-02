---
title: 'IDebugEngineProgram2:: WatchForExpressionEvaluationOnThread | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ebc513ead1ae911147217becd8f541cb11cd5585
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431477"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Permite (o no) que se produzca la evaluación de expresiones en el subproceso determinado, incluso si el programa se ha detenido.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 de Un objeto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que representa el programa que está evaluando una expresión.  
  
 `dwTid`  
 de Especifica el identificador del subproceso.  
  
 `dwEvalFlags`  
 de Combinación de marcas de la enumeración [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) que especifica cómo se va a realizar la evaluación.  
  
 `pExprCallback`  
 de Objeto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) que se va a usar para enviar eventos de depuración que se producen durante la evaluación de la expresión.  
  
 `fWatch`  
 de Si es distinto de cero ( `TRUE` ), permite la evaluación de expresiones en el subproceso identificado por `dwTid` ; de lo contrario, cero ( `FALSE` ) no permite la evaluación de expresiones en ese subproceso.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Cuando el administrador de depuración de sesión (SDM) solicita a un programa, identificado por el `pOriginatingProgram` parámetro, que evalúe una expresión, notifica a todos los demás programas asociados mediante una llamada a este método.  
  
 La evaluación de expresiones en un programa puede provocar que el código se ejecute en otro, debido a la evaluación de la función o a la evaluación de las `IDispatch` propiedades. Por este motivo, este método permite que la evaluación de expresiones se ejecute y se complete, aunque el subproceso se detenga en este programa.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
