---
title: "IActiveScriptTraceInfo::StartScriptTracing (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 90fac5ed-ce15-49b7-a6f1-605ede6f34e2
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IActiveScriptTraceInfo::StartScriptTracing (M&#233;todo)
Inicia el seguimiento del script.  
  
## Sintaxis  
  
```  
HRESULT StartScriptTracing(   
    [in] IActiveScriptSiteTraceInfo * pSiteTraceInfo,   
    [in] GUID guidContextID   
);  
  
```  
  
#### Parámetros  
 `pSiteTraceInfo`  
 Un puntero a IActiveScriptSiteTraceInfo host.  
  
 `guidContextId`  
 GUID del contexto.  
  
## Valor devuelto  
 Los valores devueltos posibles de este método son los siguientes:  
  
1.  S\_OK: Correctamente.  
  
2.  E\_POINTER: `pSiteTraceInfo` es un puntero NULL.  
  
3.  E\_NOTIMPL: no implementado.