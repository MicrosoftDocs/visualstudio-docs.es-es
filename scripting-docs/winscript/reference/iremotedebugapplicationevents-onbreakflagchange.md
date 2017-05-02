---
title: "IRemoteDebugApplicationEvents::OnBreakFlagChange | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationEvents.OnBreakFlagChange
apilocation: jscript.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationEvents::OnBreakFlagChange"
ms.assetid: 25684454-a0d8-47e0-85f5-2217069a9f45
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationEvents::OnBreakFlagChange
Controla un evento cuando cambian los marcadores de la interrupción.  
  
## Sintaxis  
  
```  
HRESULT OnBreakFlagChange(  
   APPBREAKFLAGS                   abf,  
   IRemoteDebugApplicationThread*  prdatSteppingThread  
);  
```  
  
#### Parámetros  
 `abf`  
 \[in\] la interrupción actual se marca para la aplicación.  
  
 `prdatSteppingThread`  
 \[in\] que está ejecutando el subproceso.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método controla el evento cuando el cambio de indicador de la interrupción.  
  
## Vea también  
 [IRemoteDebugApplicationEvents \(Interfaz\)](../../winscript/reference/iremotedebugapplicationevents-interface.md)   
 [APPBREAKFLAGS \(Enumeración\)](../../winscript/reference/appbreakflags-enumeration.md)