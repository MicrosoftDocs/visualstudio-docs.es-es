---
title: "IActiveScriptProfilerControl2::PrepareProfilerStop | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerControl2::PrepareProfilerStop"
ms.assetid: e43a63bc-c44f-44a8-9db4-29062b9e6a16
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptProfilerControl2::PrepareProfilerStop
Notifica al generador de perfiles que va a detener la generación de perfiles en todos los motores aplicables de script.  Con este método, puede obtener la pila de llamadas completa si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] está ejecutando cuando se deja de generar perfiles.  
  
## Sintaxis  
  
```  
HRESULT PrepareProfilerStop();  
```  
  
#### Parámetros  
 El método no toma ningún parámetro.  
  
## Valor devuelto  
 Devuelve un HRESULT.  Los valores posibles son:  
  
|Valor devuelto|Significado|  
|--------------------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_FAIL`|La generación de perfiles no pudo iniciar.|  
|`S_FALSE`|La generación de perfiles se detiene cuando un script no se ejecuta.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|La generación de perfiles no está habilitada.|  
  
## Comentarios  
 La llamada `IActiveScriptProfilerControl2::PrepareProfilerStop` garantiza que los eventos de las funciones de la pila de llamadas se envían.  Este método tiene que llamar antes de detener la generación de perfiles en el motor de script que se encuentra en la pestaña actual.  El método se puede llamar para cualquier motor de script.  
  
## Vea también  
 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)   
 [IActiveScriptProfilerControl2 \(Interfaz\)](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)