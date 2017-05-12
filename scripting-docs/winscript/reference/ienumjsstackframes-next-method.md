---
title: "IEnumJsStackFrames::Next (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumJsStackFrames.Next
apilocation: jscript9diag.dll
ms.assetid: efceb3a1-9239-4f55-9cbb-94670679988b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IEnumJsStackFrames::Next (M&#233;todo)
Obtiene el número especificado de fotogramas.  
  
## Sintaxis  
  
```  
HRESULT Next(  
   ULONG cFrameCount,  
   JS_NATIVE_FRAME *pFrames,  
   ULONG *pcFetched  
);  
```  
  
#### Parámetros  
 `cFrameCount`  
 \[in\] Número de marcos a obtener.  
  
 `pFrames`  
 \[out\] Matriz para almacenar los marcos.  
  
 `pcFetched`  
 \[out\] Número de marcos devueltos.  
  
## Valor devuelto  
  
## Requisitos  
 **Encabezado:** jscript9diag.h  
  
## Vea también  
 [IEnumJsStackFrames \(Interfaz\)](../../winscript/reference/ienumjsstackframes-interface.md)