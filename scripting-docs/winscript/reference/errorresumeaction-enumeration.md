---
title: "ERRORRESUMEACTION (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ERRORRESUMEACTION
apilocation: scrobj.dll
helpviewer_keywords: 
  - "ERRORRESUMEACTION (enumeración)"
ms.assetid: a68293c8-056b-439f-83e7-69e4a38f4976
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ERRORRESUMEACTION (Enumeraci&#243;n)
Describe cómo continuar de un error de runtime.  
  
## Sintaxis  
  
```  
typedef enum tagERRORRESUMEACTION {  
   ERRORRESUMEACTION_ReexecuteErrorStatement,  
   ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller,  
   ERRORRESUMEACTION_SkipErrorStatement,  
} ERRORRESUMEACTION;  
```  
  
## Members  
  
|Miembro|Descripción|  
|-------------|-----------------|  
|ERRORRESUMEACTION\_ReexecuteErrorStatement|Ejecute de nuevo el fragmento que generó el error.|  
|ERRORRESUMEACTION\_AbortCallAndReturnErrorToCaller|Permite el motor de lenguaje controlar el error.|  
|ERRORRESUMEACTION\_SkipErrorStatement|Reanuda la ejecución del código que sigue al extraer que generó el error.|  
  
## Vea también  
 [Active Script Debugger \(Constantes, enumeraciones y estructuras\)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)