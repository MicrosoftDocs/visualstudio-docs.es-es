---
title: "IActiveScriptSiteUIControl::GetUIBehavior (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 9a944335-856a-4c6b-b2bc-8872542941b7
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# IActiveScriptSiteUIControl::GetUIBehavior (M&#233;todo)
Obtiene [SCRIPTUICHANDLING \(Enumeración\)](../../winscript/reference/scriptuichandling-enumeration.md) que representa la manera en que un control de IU debe controlar.  
  
## Sintaxis  
  
```  
HRESULT GetUIBehavior(   
    [in] SCRIPTUICITEM UicItem,   
    [out] SCRIPTUICHANDLING * pUicHandling   
);  
  
```  
  
#### Parámetros  
 `UicItem`  
 Tipo del control.  
  
 `pUicHandling`  
 El modo en que el control debe controlarse.