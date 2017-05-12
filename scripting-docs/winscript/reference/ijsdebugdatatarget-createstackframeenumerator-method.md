---
title: "IJsDebugDataTarget::CreateStackFrameEnumerator (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.CreateStackFrameEnumerator
apilocation: jscript9diag.dll
ms.assetid: cda172e5-18d0-43c5-81d8-432ab30ee70d
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::CreateStackFrameEnumerator (M&#233;todo)
Crea un enumerador para los marcos de pila.  
  
## Sintaxis  
  
```  
HRESULT CreateStackFrameEnumerator(  
   DWORD threadId,  
   IEnumJsStackFrames **ppEnumerator  
);  
```  
  
#### Parámetros  
 `threadId`  
 \[in\] Subproceso que se está ejecutando en el proceso de destino.  
  
 `ppEnumerator`  
 \[out\] Enumerador para marcos de pila.  
  
## Valor devuelto  
  
## Requisitos  
 **Encabezado:** jscript9diag.h  
  
## Vea también  
 [IJsDebugDataTarget \(Interfaz\)](../../winscript/reference/ijsdebugdatatarget-interface.md)