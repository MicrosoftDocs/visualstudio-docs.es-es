---
title: "IDebugApplication::HandleBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.HandleBreakPoint
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::HandleBreakPoint"
ms.assetid: 97219bdf-a39a-4e69-81ac-4ca2afe77ce5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::HandleBreakPoint
Hace que el subproceso actual para bloquear y envía una notificación de punto de interrupción al depurador el IDE.  
  
## Sintaxis  
  
```  
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### Parámetros  
 `br`  
 \[in\] motivo de la interrupción.  
  
 `pbra`  
 \[out\] acción para tomar cuando el depurador reanuda la aplicación.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Un motor de lenguaje llama a este método en el contexto de un subproceso que alcance un punto de interrupción.  Este método bloquea el subproceso actual y envía una notificación de punto de interrupción al depurador el IDE.  Cuando el depurador reanuda la aplicación, el parámetro de `pbra` especifica la acción que se va a realizar.  
  
> [!NOTE]
>  El motor de idioma se puede llamar el subproceso para realizar tareas como enumera los marcos de pila o evalúa las expresiones durante el punto de interrupción.  
  
 Este método hace que `IApplicationDebugger::onHandleBreakPoint` que se va a llamar.  
  
## Vea también  
 [IDebugApplication \(Interfaz\)](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
 [BREAKREASON \(Enumeración\)](../../winscript/reference/breakreason-enumeration.md)   
 [BREAKRESUMEACTION \(Enumeración\)](../../winscript/reference/breakresumeaction-enumeration.md)