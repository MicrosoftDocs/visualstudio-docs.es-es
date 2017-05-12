---
title: "SCRIPTUICITEM (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: fbf01f1b-5d7f-4d92-8d10-3da65e352d93
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# SCRIPTUICITEM (Enumeraci&#243;n)
Representa el tipo de elemento de la interfaz de usuario.  Utilizado en [IActiveScriptSiteUIControl::GetUIBehavior \(Método\)](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md).  
  
## Sintaxis  
  
```vb  
typedef enum tagSCRIPTUICITEM {   
    SCRIPTUICITEM_INPUTBOX = 1,   
    SCRIPTUICITEM_MSGBOX = 2,   
    } SCRIPTUICITEM;  
  
```  
  
## Valores de enumeración  
  
|||  
|-|-|  
|SCRIPTUICITEM\_INPUTBOX|Un control.|  
|SCRIPTUICITEM\_MSGBOX|Un cuadro de mensaje.|