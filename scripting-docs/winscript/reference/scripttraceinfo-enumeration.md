---
title: "SCRIPTTRACEINFO (enumeración) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: cb8a4767-8c8e-4fa0-a735-038767a8c500
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc1902b290a8024679cef12d503e94de4923defb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="scripttraceinfo-enumeration"></a>SCRIPTTRACEINFO (Enumeración)
Representa el evento de secuencia de comandos que se realiza un seguimiento. Utilizado en el [método iactivescriptsitetraceinfo:: Sendscripttraceinfo](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef enum tagSCRIPTTRACEINFO {      SCRIPTTRACEINFO_SCRIPTSTART = 0,      SCRIPTTRACEINFO_SCRIPTEND   = 1,      SCRIPTTRACEINFO_COMCALLSTART    = 2,      SCRIPTTRACEINFO_COMCALLEND  = 3,      SCRIPTTRACEINFO_CREATEOBJSTART  = 4,      SCRIPTTRACEINFO_CREATEOBJEND    = 5,      SCRIPTTRACEINFO_GETOBJSTART = 6,      SCRIPTTRACEINFO_GETOBJEND   = 7,  } SCRIPTTRACEINFO ;  
```  
  
## <a name="enumeration-values"></a>Valores de enumeración  
  
|||  
|-|-|  
|SCRIPTTRACEINFO_SCRIPTSTART|El inicio de una secuencia de comandos.|  
|SCRIPTTRACEINFO_SCRIPTEND|El final de la secuencia de comandos.|  
|SCRIPTTRACEINFO_COMCALLSTART|El inicio de una llamada de COM.|  
|SCRIPTTRACEINFO_COMCALLEND|El final de una llamada de COM.|  
|SCRIPTTRACEINFO_CREATEOBJSTART|El inicio de creación de objetos.|  
|SCRIPTTRACEINFO_CREATEOBJEND|El extremo de creación de objetos.|  
|SCRIPTTRACEINFO_GETOBJSTART|El inicio de una llamada GetObject.|  
|SCRIPTTRACEINFO_GETOBJEND|El final de una llamada GetObject.|