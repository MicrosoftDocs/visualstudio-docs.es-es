---
title: "IJsDebugProcess::CreateBreakPoint (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugProcess.CreateBreakPoint
apilocation: jscript9diag.dll
ms.assetid: a2cb4233-2846-4d11-aa13-21de43abda9f
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IJsDebugProcess::CreateBreakPoint (M&#233;todo)
Establece el punto de interrupción en la posición del documento especificada.  
  
## Sintaxis  
  
```  
HRESULT CreateBreakPoint(  
   UINT64 documentId,  
   DWORD characterOffset,  
   DWORD characterCount,  
   BOOL isEnabled,  
   IJsDebugBreakPoint **ppDebugBreakPoint  
);  
```  
  
#### Parámetros  
 `documentId`  
 \[in\] Puntero a IDebugDocumentText.  
  
 `characterOffset`  
 \[in\] Desplazamiento de caracteres desde el principio del archivo.  
  
 `characterCount`  
 \[in\] Longitud del texto del documento dentro del que se debe insertar el punto de interrupción.  
  
 `isEnabled`  
 \[in\] Especifica si el punto de interrupción está habilitado.  
  
 `ppDebugBreakPoint`  
 \[out\] Objeto que representa el punto de interrupción creado.  
  
## Valor devuelto  
  
## Requisitos  
 **Encabezado:** jscript9diag.h  
  
## Vea también  
 [IJsDebugProcess \(Interfaz\)](../../winscript/reference/ijsdebugprocess-interface.md)