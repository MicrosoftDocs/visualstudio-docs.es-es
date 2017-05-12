---
title: "IActiveScriptProfilerControl2::CompleteProfilerStart | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerControl2::CompleteProfilerStart"
ms.assetid: e14d94a2-39d3-40a1-84d9-6300fbe2b339
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptProfilerControl2::CompleteProfilerStart
Notifica al generador de perfiles que ha iniciado la generación de perfiles en todos los motores aplicables de script.  Con este método, puede obtener la pila de llamadas completa si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] se ejecuta al iniciar la generación de perfiles.  
  
## Sintaxis  
  
```  
HRESULT CompleteProfilerStart();  
```  
  
#### Parámetros  
 El método no toma ningún parámetro.  
  
## Valor devuelto  
 Devuelve un HRESULT.  Los valores posibles son:  
  
|Valor devuelto|Significado|  
|--------------------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_FAIL`|La generación de perfiles no puede iniciar.|  
|`S_FALSE`|La generación de perfiles se inicia cuando un script no se ejecuta.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|La generación de perfiles no está habilitada.  No se ha establecido ningún devolución.|  
|`E_OUTOFMEMORY`|La pila de llamadas no se puede obtener debido a una condición de hacia fuera\-de\-memoria.|  
  
## Comentarios  
 La llamada `IActiveScriptProfilerControl2::CompleteProfilerStart` garantiza que los eventos de las funciones ya en la pila de llamadas se envían.  Este método tiene que llamar después de generar perfiles empieza en cualquier motor de script que se encuentra en la pestaña actual.  El método se puede llamar para cualquier motor de script.  
  
## Vea también  
 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)   
 [IActiveScriptProfilerControl2 \(Interfaz\)](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)