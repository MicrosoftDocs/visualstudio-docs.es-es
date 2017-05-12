---
title: "IEnumRemoteDebugApplicationThreads::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumRemoteDebugApplicationThreads.Skip
apilocation: pdm.dll
helpviewer_keywords: 
  - "IEnumRemoteDebugApplicationThreads::Skip"
ms.assetid: bb13a18b-bcf8-4542-8b1a-55a4f2769536
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumRemoteDebugApplicationThreads::Skip
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
 [IEnumRemoteDebugApplicationThreads \(Interfaz\)](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)