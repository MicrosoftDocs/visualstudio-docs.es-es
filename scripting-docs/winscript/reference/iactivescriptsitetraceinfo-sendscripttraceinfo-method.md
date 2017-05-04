---
title: "IActiveScriptSiteTraceInfo::SendScriptTraceInfo (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 0419e4c5-eb7c-45a3-b6dc-1a5e157d95f9
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IActiveScriptSiteTraceInfo::SendScriptTraceInfo (M&#233;todo)
Envía la información de traza que incluye el tipo de evento, contexto, y la instrucción del script.  
  
## Sintaxis  
  
```  
HRESULT SendScriptTraceInfo(   
    [in] SCRIPTTRACEINFO stiEventType,   
    [in] GUID guidContextID,   
    [in] DWORD dwScriptContextCookie,   
    [in] LONG lScriptStatementStart,   
    [in] LONG lScriptStatementEnd,   
    [in] DWORD64 dwReserved   
);   
```  
  
#### Parámetros  
 `stiEventType`  
 Tipo de evento.  
  
 `guidContextId`  
 GUID del contexto.  
  
 `dwScriptContextCookie`  
 La cookie del contexto.  
  
 `lScriptStatementStart`  
 La ubicación de inicio de la instrucción del script.  
  
 `lScriptStatementEnd`  
 La ubicación del final de la instrucción del script.  
  
 `dwReserved`  
 Reservado.