---
title: "APPLICATION_NODE_EVENT_FILTER (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "APPLICATION_NODE_EVENT_FILTER (Constantes)"
ms.assetid: dccb2cf7-0598-46f8-b3eb-16b752815e96
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# APPLICATION_NODE_EVENT_FILTER (Enumeraci&#243;n)
Especifica los tipos de nodos excluir cuando filtra codifique los documentos.  Utilizado en [IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) y [IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
>  Estas constantes se implementan como PDM v10.0 y mayor.  Encontrado en activdbg100.h.  
  
## Sintaxis  
  
```cpp  
typedef enum tagAPPLICATION_NODE_EVENT_FILTER {  
    FILTER_EXCLUDE_NOTHING = 0,  
    FILTER_EXCLUDE_ANONYMOUS_CODE = 0x1,  
    FILTER_EXCLUDE_EVAL_CODE = 0x2  
} APPLICATION_NODE_EVENT_FILTER;  
  
```  
  
## Members  
  
|Miembro|Valor|Descripción|  
|-------------|-----------|-----------------|  
|FILTER\_EXCLUDE\_NOTHING|0x00000000|Envíe todos los eventos.|  
|FILTER\_EXCLUDE\_ANONYMOUS\_CODE|0x00000001|Excluya los nodos anónimos de código.  Estos nodos se utilizan por el runtime de JScript para `new Function([args,] <code>)'`.|  
|FILTER\_EXCLUDE\_EVAL\_CODE|0x00000002|Excluya los nodos eval de código.  Estos nodos se utilizan por el runtime de JScript para compatibilidad eval.|  
  
## Vea también  
 [Active Script Debugger \(Constantes, enumeraciones y estructuras\)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)