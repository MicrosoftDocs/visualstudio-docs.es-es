---
title: "IRemoteDebugApplication::ResumeFromBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.ResumeFromBreakPoint
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::ResumeFromBreakPoint"
ms.assetid: a613cc2b-1d69-4713-a235-64372c253b4a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::ResumeFromBreakPoint
Continúa una aplicación que está actualmente en un punto de interrupción.  
  
## Sintaxis  
  
```  
HRESULT ResumeFromBreakPoint(  
   IRemoteDebugApplicationThread*  prptFocus,  
   BREAKRESUMEACTION               bra,  
   ERRORRESUMEACTION               era  
);  
```  
  
#### Parámetros  
 `prptFocus`  
 \[in\] modos de recorrido For, el subproceso que debe ser afectado por el modo de entrada.  
  
 `bra`  
 \[in\] acción para obtener tomar sobre reanudar la aplicación.  
  
 `era`  
 \[in\] acción de The para admitir el caso que la aplicación se detuvo debido a un error.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método continúa una aplicación que está actualmente en un punto de interrupción.  
  
## Vea también  
 [IRemoteDebugApplication \(Interfaz\)](../../winscript/reference/iremotedebugapplication-interface.md)   
 [BREAKRESUMEACTION \(Enumeración\)](../../winscript/reference/breakresumeaction-enumeration.md)   
 [ERRORRESUMEACTION \(Enumeración\)](../../winscript/reference/errorresumeaction-enumeration.md)