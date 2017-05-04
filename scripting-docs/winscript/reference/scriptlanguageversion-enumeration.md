---
title: "SCRIPTLANGUAGEVERSION (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 58aa904a-e3ed-41c6-82d6-e91c8279a792
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# SCRIPTLANGUAGEVERSION (Enumeraci&#243;n)
Especifica las versiones del script.  
  
## Sintaxis  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION  
{  
    SCRIPTLANGUAGEVERSION_DEFAULT = 0,  
    SCRIPTLANGUAGEVERSION_5_7  = 1,  
    SCRIPTLANGUAGEVERSION_5_8  = 2,  
    SCRIPTLANGUAGEVERSION_MAX  = 255  
} SCRIPTLANGUAGEVERSION ;  
  
```  
  
## Valores de enumeración  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION\_DEFAULT|La versión predeterminada.  El valor entero es 0.|  
|SCRIPTLANGUAGEVERSION\_5\_7|Versión 5,7 de script de Windows.  El valor entero es 1.|  
|SCRIPTLANGUAGEVERSION\_5\_8|Versión 5,8 de script de Windows.  El valor entero es 2.|  
|SCRIPTLANGUAGEVERSION\_MAX|La versión máxima.  El valor entero es 255.|  
  
## Vea también  
 [Active Script \(constantes, enumeraciones y códigos de error\)](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)