---
title: "IDebugStackFrameSniffer::EnumStackFrames | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugStackFrameSniffer.EnumStackFrames
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugStackFrameSniffer::EnumStackFrames"
ms.assetid: a7629ab3-ef7d-4bbe-a137-bb2a8ad0f384
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrameSniffer::EnumStackFrames
Devuelve un enumerador de los marcos de pila del subproceso actual.  
  
## Sintaxis  
  
```  
HRESULT EnumStackFrames(  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### Parámetros  
 `ppedsf`  
 \[out\] enumerador de los marcos de pila del subproceso actual.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 El enumerador del marco de pila devuelve los marcos que comienza en la parte superior de la pila, empezando por el cuadro recientemente presionado.  
  
## Vea también  
 [IDebugStackFrameSniffer \(Interfaz\)](../../winscript/reference/idebugstackframesniffer-interface.md)