---
title: "IActiveScript::InterruptScriptThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.InterruptScriptThread
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_InterruptScriptThread"
ms.assetid: 2304d035-6d39-4811-acd3-8a9640fdbef6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::InterruptScriptThread
Detiene la ejecución de un subproceso en ejecución de script \(receptor de eventos, una ejecución inmediata, o una llamada de macro\).  Este método se puede utilizar para finalizar un script que está bloqueado \(por ejemplo, en un bucle sin fin\).  Puede ser llamado desde los subprocesos de la interfaz no base fuera lo que da como resultado una llamada no base para hospedar objetos o al método de [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## Sintaxis  
  
```  
HRESULT InterruptScriptThread(  
    SCRIPTTHREADID   stidThread,  // identifier of thread  
    const EXCEPINFO *pexcepinfo,  // receives error information  
    DWORD dwFlags  
);  
```  
  
#### Parámetros  
 `stidThread`  
 \[in\] identificador del subproceso interrumpir, o uno de identificador especial siguiente de subproceso valora:  
  
|Valor|Significado|  
|-----------|-----------------|  
|SCRIPTTHREADID\_ALL|Todos los subprocesos.  La interrupción se aplica a todos los métodos de script actualmente en curso.  Observe que a menos que el autor de llamada ha solicitado que el script es desconectado, la secuencia de comandos script siguiente de las causas de evento para ejecutarse de nuevo llamando al método de [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) con el SCRIPTSTATE\_DISCONNECTED o SCRIPTSTATE\_INITIALIZED marcan el conjunto.|  
|SCRIPTTHREADID\_BASE|El subproceso base; es decir, el subproceso en el que el motor de script se creó instancias.|  
|SCRIPTTHREADID\_CURRENT|El subproceso que se está ejecutando actualmente.|  
  
 `pexcepinfo`  
 \[in\] dirección de una estructura de `EXCEPINFO` que contiene información de error que se debe señalar al script anulado.  
  
 `dwFlags`  
 \[in\] marcadores de opciones asociadas a la interrupción.  Puede ser uno de los valores siguientes:  
  
|Valor|Significado|  
|-----------|-----------------|  
|SCRIPTINTERRUPT\_DEBUG|Si se admite, escriba el depurador del motor de script en el punto de ejecución actual del script.|  
|SCRIPTINTERRUPT\_RAISEEXCEPTION|Si lo admite el lenguaje del motor de scripting, deje el script controlar la excepción.  Si no, el método de script se anula y el código de error se devuelve al llamador; es decir, el solicitante del origen de eventos o de la macro.|  
  
## Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|--------------------|-----------------|  
|`S_OK`|Correcto.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_POINTER`|Un puntero no válido se especificado.|  
|`E_UNEXPECTED`|La llamada no se esperaba \(por ejemplo, el motor de script aún no se han cargado no se ha inicializado\).|  
  
## Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)