---
title: "SCRIPTTRACEINFO (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: cb8a4767-8c8e-4fa0-a735-038767a8c500
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# SCRIPTTRACEINFO (Enumeraci&#243;n)
Representa el evento de script se está realizando paso a paso que.  Utilizado en [IActiveScriptSiteTraceInfo::SendScriptTraceInfo \(Método\)](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).  
  
## Sintaxis  
  
```  
typedef enum tagSCRIPTTRACEINFO {    
    SCRIPTTRACEINFO_SCRIPTSTART = 0,    
    SCRIPTTRACEINFO_SCRIPTEND   = 1,    
    SCRIPTTRACEINFO_COMCALLSTART    = 2,    
    SCRIPTTRACEINFO_COMCALLEND  = 3,    
    SCRIPTTRACEINFO_CREATEOBJSTART  = 4,    
    SCRIPTTRACEINFO_CREATEOBJEND    = 5,    
    SCRIPTTRACEINFO_GETOBJSTART = 6,    
    SCRIPTTRACEINFO_GETOBJEND   = 7,    
} SCRIPTTRACEINFO ;  
```  
  
## Valores de enumeración  
  
|||  
|-|-|  
|SCRIPTTRACEINFO\_SCRIPTSTART|El inicio de un script.|  
|SCRIPTTRACEINFO\_SCRIPTEND|El final del script.|  
|SCRIPTTRACEINFO\_COMCALLSTART|El inicio de una llamada COM.|  
|SCRIPTTRACEINFO\_COMCALLEND|El final de una llamada COM.|  
|SCRIPTTRACEINFO\_CREATEOBJSTART|El inicio de la creación de objetos.|  
|SCRIPTTRACEINFO\_CREATEOBJEND|El extremo de la creación de objetos.|  
|SCRIPTTRACEINFO\_GETOBJSTART|El inicio de una llamada GetObject.|  
|SCRIPTTRACEINFO\_GETOBJEND|El final de una llamada GetObject.|