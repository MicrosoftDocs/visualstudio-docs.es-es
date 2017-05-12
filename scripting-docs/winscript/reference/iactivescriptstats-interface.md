---
title: "IActiveScriptStats (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptStats (interfaz)"
ms.assetid: dbe84d6f-1b77-4877-aced-cd4e01ead5b5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptStats (Interfaz)
Permite que un host vea las estadísticas de un script en ejecución.  El host puede utilizar esta información para determinar si el script ha llevado demasiado tiempo completo.  
  
 Además de los métodos heredados de `IUnknown`, la interfaz `IActiveScriptStats` expone los métodos siguientes.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)|Especificado uno de las estadísticas estándar del script.|  
|[IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)|Devuelve estadísticas personalizada del script.|  
|[IActiveScriptStats::ResetStats](../../winscript/reference/iactivescriptstats-resetstats.md)|Restablece las estadísticas para este script.|