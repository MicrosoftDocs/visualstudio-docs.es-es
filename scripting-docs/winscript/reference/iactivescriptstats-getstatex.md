---
title: "IActiveScriptStats::GetStatEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptStats.GetStatEx
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptStats::GetStatEx"
ms.assetid: f526f51d-8ab5-49ef-a8f7-ae0ac1cb46e4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptStats::GetStatEx
Devuelve estadísticas personalizada del script.  
  
## Sintaxis  
  
```  
HRESULT GetStatEx(  
   REFGUID  guid,  
   ULONG*   pluHi,  
   ULONG*   pluLo  
);  
```  
  
#### Parámetros  
 `guid`  
 \[in\] especifica que estadística a devolver.  La semántica de la estadística corresponde al GUID determinado es totalmente motor definido.  
  
 `pluHi`  
 \[out\] bits height 32 de un entero sin signo de 64 bits que representa la estadística.  
  
 `pluLo`  
 \[out\] bits bajos de El 32 de un entero sin signo de 64 bits que representa la estadística.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_NOTIMPL`|Este método no está implementado.|  
  
## Comentarios  
 Este método permite que un motor de script personalizado devuelve estadísticas significativas a un host de personalizadas.  
  
> [!NOTE]
>  Este método no está implementado actualmente.  
  
## Vea también  
 [IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)   
 [IActiveScriptStats \(Interfaz\)](../../winscript/reference/iactivescriptstats-interface.md)