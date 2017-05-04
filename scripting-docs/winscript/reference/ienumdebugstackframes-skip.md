---
title: "IEnumDebugStackFrames::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugStackFrames.Skip
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugStackFrames::Skip"
ms.assetid: d893d6e9-e119-4f14-99d0-bf23dbd2d625
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugStackFrames::Skip
Omite un número especificado de segmentos en una secuencia de enumeración.  
  
## Sintaxis  
  
```  
HRESULT Skip(  
   ULONG  celt  
);  
```  
  
#### Parámetros  
 `celt`  
 \[in\] número de segmentos de la secuencia de enumeración al salto.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método omite un número especificado de segmentos en una secuencia de enumeración.  
  
## Vea también  
 [IEnumDebugStackFrames \(Interfaz\)](../../winscript/reference/ienumdebugstackframes-interface.md)