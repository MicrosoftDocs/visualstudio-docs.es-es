---
title: "IActiveScriptStats::GetStat | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptStats.GetStat
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptStats::GetStat"
ms.assetid: 31fd15b3-0713-4b55-b4f7-bfd7ea198493
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptStats::GetStat
Especificado uno de las estadísticas estándar del script.  
  
## Sintaxis  
  
```  
HRESULT GetStat(  
   DWORD   stid,  
   ULONG*  pluHi,  
   ULONG*  pluLo  
);  
```  
  
#### Parámetros  
 `stid`  
 \[in\] especifica que estadística a devolver.  Debe ser el valor:  
  
|Constante|Valor|Descripción|  
|---------------|-----------|-----------------|  
|SCRIPTSTAT\_STATEMENT\_COUNT|1|Devuelve el número de extractos ejecutados desde el script iniciado o las estadísticas se ha restaurado.|  
  
 `pluHi`  
 \[out\] bits height 32 de un entero sin signo de 64 bits que representa la estadística.  
  
 `pluLo`  
 \[out\] bits bajos de El 32 de un entero sin signo de 64 bits que representa la estadística.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a los valores de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método devuelve una de las estadísticas estándar del script.  
  
## Vea también  
 [IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)   
 [IActiveScriptStats \(Interfaz\)](../../winscript/reference/iactivescriptstats-interface.md)