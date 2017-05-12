---
title: "IActiveScriptProfilerCallback::Initialize | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.Initialize
apilocation: scrobj.dll
ms.assetid: a257111e-a50b-4962-9dd6-c893d40f6985
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptProfilerCallback::Initialize
Denominado para inicializar el objeto de generador de perfiles siempre que genera un perfil se inicie en un motor de script.  
  
## Sintaxis  
  
```  
HRESULT Initialize(  
    [in] DWORD dwContext);  
```  
  
#### Parámetros  
 `dwContext`  
 \[in\] Al valor de 4 bytes que se pasa a [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md).  
  
## Valor devuelto  
 Devuelve un HRESULT.  Los valores posibles son:  
  
|Valor devuelto|Significado|  
|--------------------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Si el método no puede inicializar el objeto de generador de perfiles, debe devolver un error HRESULT notificar al motor de script.  En este caso, el motor de script debe llamar directamente [IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md), pasando el HRESULT en el parámetro y, a continuación libera el objeto de generador de perfiles.  
  
## Vea también  
 [IActiveScriptProfilerCallback \(Interfaz\)](../../winscript/reference/iactivescriptprofilercallback-interface.md)