---
title: "IDebugEngineProgram2::WatchForExpressionEvaluationOnThread | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineProgram2::WatchForExpressionEvaluationOnThread"
helpviewer_keywords: 
  - "IDebugEngineProgram2::WatchForExpressionEvaluationOnThread"
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Permite o deniega\) la evaluación de la expresión aparece en el subproceso especificado, aunque el programa ha detenido.  
  
## Sintaxis  
  
```cpp#  
HRESULT WatchForExpressionEvaluationOnThread(   
   IDebugProgram2*       pOriginatingProgram,  
   DWORD                 dwTid,  
   DWORD                 dwEvalFlags,  
   IDebugEventCallback2* pExprCallback,  
   BOOL                  fWatch  
);  
```  
  
```c#  
int WatchForExpressionEvaluationOnThread(   
   IDebugProgram2       pOriginatingProgram,  
   uint                  dwTid,  
   uint                  dwEvalFlags,  
   IDebugEventCallback2 pExprCallback,  
   int                   fWatch  
);  
```  
  
#### Parámetros  
 `pOriginatingProgram`  
 \[in\]  Un objeto de [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que representa el programa que se está evaluando una expresión.  
  
 `dwTid`  
 \[in\]  Especifica el identificador del subproceso.  
  
 `dwEvalFlags`  
 \[in\]  Una combinación de marcadores de enumeración de [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) que especifican cómo la evaluación debe realizar.  
  
 `pExprCallback`  
 \[in\]  Un objeto de [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) que se utilizará para enviar los eventos de depuración que se producen durante la evaluación de la expresión.  
  
 `fWatch`  
 \[in\]  Si es distinto de cero \(`TRUE`\), permite la evaluación de expresiones en el subproceso identificado por `dwTid`; si no, cero \(`FALSE`\) deniega la evaluación de expresiones en ese subproceso.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Cuando el administrador de depuración de sesión \(SDM\) solicita un programa, identificado por el parámetro de `pOriginatingProgram` , evaluar una expresión, notifica al resto de los programas asociados llamando a este método.  
  
 La evaluación de expresiones en un programa puede hacer que el código se ejecute en otro, debido a la evaluación de la función o a la evaluación de cualquier propiedad de `IDispatch` .  debido a esto, este método permite que la evaluación de la expresión ejecute y complete aunque el subproceso se puede detener en este programa.  
  
## Vea también  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)