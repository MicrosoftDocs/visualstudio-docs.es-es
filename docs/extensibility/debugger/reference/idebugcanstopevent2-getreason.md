---
title: "IDebugCanStopEvent2::GetReason | Microsoft Docs"
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
  - "IDebugCanStopEvent2::GetReason"
helpviewer_keywords: 
  - "IDebugCanStopEvent2::GetReason"
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCanStopEvent2::GetReason
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el motivo por el que el motor de depuración \(DE\) desea detener.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetReason(   
   CANSTOP_REASON* pcr  
);  
```  
  
```c#  
int GetReason(   
   out enum_CANSTOP_REASON pcr  
);  
```  
  
#### Parámetros  
 `pcr`  
 \[out\]  Devuelve un valor de enumeración de [CANSTOP\_REASON](../../../extensibility/debugger/reference/canstop-reason.md) que describe el motivo de este evento.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Este método se llama normalmente antes del método de [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) por lo que el llamador puede determinar si pasar distinto de cero \(`TRUE`\) al método de `IDebugCanStopEvent2::CanStop` .  
  
 La razón de detener puede ser cualquier `CANSTOP_ENTRYPOINT`, que significa que el OF ha alcanzado un punto de entrada, o `CANSTOP_STEPIN`, que significa el OF ha ejecutado en una función.  
  
## Vea también  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [CANSTOP\_REASON](../../../extensibility/debugger/reference/canstop-reason.md)   
 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)