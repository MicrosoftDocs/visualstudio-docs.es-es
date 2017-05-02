---
title: "IJsDebugDataTarget::GetThreadContext (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.GetThreadContext
apilocation: jscript9diag.dll
ms.assetid: faf2a689-6c49-4a7d-b5a6-2b323e2257a7
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::GetThreadContext (M&#233;todo)
Recupera contexto para el subproceso especificado.  
  
## Sintaxis  
  
```  
HRESULT GetThreadContext(  
   DWORD threadId,  
   ULONG32 contextFlags,  
   ULONG32 contextSize,  
   void *pContext  
);  
```  
  
#### Parámetros  
 `threadId`  
 \[in\] Subproceso que se está ejecutando en el proceso de destino.  
  
 `contextFlags`  
 \[in\] Especifica marcadores de contexto.  Esto equivale al campo ContextFlags de CONTEXT \(para obtener más información, vea winnt.h y busque CONTEXT\_ALL\).  
  
 `contextSize`  
 \[in\] Tamaño del búfer especificado por pContext.  
  
 `pContext`  
 \[out\] Recibe la estructura CONTEXT específica de la plataforma en el búfer especificado por pContext.  
  
## Valor devuelto  
  
## Requisitos  
 **Encabezado:** jscript9diag.h  
  
## Vea también  
 [IJsDebugDataTarget \(Interfaz\)](../../winscript/reference/ijsdebugdatatarget-interface.md)