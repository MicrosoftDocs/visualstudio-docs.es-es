---
title: "IActiveScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScript (interfaz)"
ms.assetid: d8acee11-7f0d-4999-b97a-66774af16f71
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript
Proporciona los métodos necesarios para inicializar el motor de script.  El motor de script debe implementar la interfaz de `IActiveScript` .  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|Informa al motor de script el sitio de [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) proporcionado por el host.|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|Recupera el objeto de sitio asociado al motor de scripts de Windows.|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|Coloca el motor de script en el estado especificado.|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|Recupera el estado actual del motor de script.|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|Hace que el motor de script para abandonar cualquier script actualmente cargado, para perder su estado, y liberar los punteros de interfaz que tenga que otros objetos, lo escribiendo en un estado cerrado.|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|Agrega el nombre de un elemento de nivel raíz al espacio de nombres del motor de script.|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|Agrega una biblioteca de tipos al espacio de nombres para el script.|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|Recupera la interfaz de `IDispatch` para el script actual.|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|Recupera un identificador script\-motor\- definido para el subproceso que se está ejecutando actualmente.|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|Recupera un identificador script\-motor\- definido para el subproceso asociado al subproceso determinado de Microsoft Win32.|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|Recupera el estado actual de un subproceso del script.|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|Detiene la ejecución de un subproceso en ejecución del script.|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|Clona el motor de scripting actual \(menos cualquier estado de ejecución actual\), y devuelve un motor carga de script que no tiene ningún sitio en el subproceso actual.|  
  
## Vea también  
 [Referencia de interfaces de Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)