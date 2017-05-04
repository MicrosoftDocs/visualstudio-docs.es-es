---
title: "IEnumDebugStackFrames::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugStackFrames.Next
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugStackFrames::Next"
ms.assetid: ade3f5b0-8ff3-48a0-9433-270789e6d53e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugStackFrames::Next
Recupera un número especificado de segmentos de la secuencia de la enumeración.  
  
## Sintaxis  
  
```  
HRESULT Next(  
   ULONG                       celt,  
   DebugStackFrameDescriptor*  prgdsfd,  
   ULONG*                      pceltFetched  
);  
```  
  
#### Parámetros  
 `celt`  
 \[in\] número de segmentos a recuperar.  
  
 `prgdsfd`  
 \[out\] devuelve una matriz de las interfaces de `DebugStackFrameDescriptor` que representa los segmentos que se recuperan.  
  
 `pceltFetched`  
 \[out\] número real de segmentos capturados por el enumerador.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método recupera un número especificado de segmentos de la secuencia de la enumeración.  
  
## Vea también  
 [IEnumDebugStackFrames \(Interfaz\)](../../winscript/reference/ienumdebugstackframes-interface.md)   
 [DebugStackFrameDescriptor \(Estructura\)](../../winscript/reference/debugstackframedescriptor-structure.md)