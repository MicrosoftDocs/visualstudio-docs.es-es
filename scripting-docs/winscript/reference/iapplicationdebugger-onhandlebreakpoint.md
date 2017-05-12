---
title: "IApplicationDebugger::onHandleBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebugger.onHandleBreakPoint
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebugger::onHandleBreakPoint"
ms.assetid: 31adcecd-d6c1-4222-ab2c-32ec2fefb322
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebugger::onHandleBreakPoint
Controla un evento de punto de interrupción.  
  
## Sintaxis  
  
```  
HRESULT onHandleBreakPoint(  
   IRemoteDebugApplicationThread*  prpt,  
   BREAKREASON                     br,  
   IActiveScriptErrorDebug*        pError  
);  
```  
  
#### Parámetros  
 `prpt`  
 \[in\] subproceso se donde el punto de interrupción.  
  
 `br`  
 \[in\] motivo del punto de interrupción.  
  
 `pError`  
 \[in\] información de error de runtime, siempre y cuando el valor de `br` es BREAKREASON\_ERROR.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Se llama a este método cuando se alcance un punto de interrupción y se denomina `IDebugApplication::HandleBreakPoint` .  
  
 La aplicación permanecerá suspendida hasta que el depurador IDE llame a `IRemoteDebugApplication::ResumeFromBreakPoint`.  
  
## Vea también  
 [IApplicationDebugger \(Interfaz\)](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)   
 [IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)   
 [BREAKREASON \(Enumeración\)](../../winscript/reference/breakreason-enumeration.md)