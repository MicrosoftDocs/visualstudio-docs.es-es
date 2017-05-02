---
title: "IEnumDebugApplicationNodes::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugApplicationNodes.Skip
apilocation: pdm.dll
helpviewer_keywords: 
  - "IEnumDebugApplicationNodes::Skip"
ms.assetid: b2ad1957-95b5-4c09-9a44-5a765a5308ae
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugApplicationNodes::Skip
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
 [IEnumDebugApplicationNodes \(Interfaz\)](../../winscript/reference/ienumdebugapplicationnodes-interface.md)