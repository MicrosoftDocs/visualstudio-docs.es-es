---
title: "IRemoteDebugApplicationEx:ForceStepMode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationEx:ForceStepMode
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationEx:ForceStepMode"
ms.assetid: 83e69a3e-e4c9-4ddd-b01b-1820e4177a03
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IRemoteDebugApplicationEx:ForceStepMode
Fuerza el depurador en modo paso a paso.  
  
## Sintaxis  
  
```  
HRESULT ForceStepMode(  
   IRemoteDebugApplicationThread*  pStepThread  
);  
```  
  
#### Parámetros  
 `pStepThread`  
 \[in\] subproceso para la depuración de procesos Monitor a recorrer.  Si es NULL, el PDM borra el subproceso de recorrido.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
  
## Vea también  
 [IRemoteDebugApplicationEx Interface](http://msdn.microsoft.com/es-es/2f65fa67-06b7-4053-8945-22383ab66343)