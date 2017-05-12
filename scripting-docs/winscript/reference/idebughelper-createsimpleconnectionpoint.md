---
title: "IDebugHelper::CreateSimpleConnectionPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugHelper.CreateSimpleConnectionPoint
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugHelper::CreateSimpleConnectionPoint"
ms.assetid: 5e4798ce-6f9f-4184-9853-67bf8c8524ab
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugHelper::CreateSimpleConnectionPoint
Devuelve una interfaz de eventos que contenga un objeto determinado de `IDispatch` .  
  
## Sintaxis  
  
```  
HRESULT CreateSimpleConnectionPoint(  
   IDispatch*                pdisp   
   ISimpleConnectionPoint**  ppscp  
);  
```  
  
#### Parámetros  
 `pdisp`  
 \[in\] objeto de El `IDispatch` el ajuste.  
  
 `ppscp`  
 \[out\] interfaz de eventos a El que contiene `pdisp`.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Devuelve una interfaz de eventos que ajuste `IDispatch` determinado \(vea [ISimpleConnectionPoint \(Interfaz\)](../../winscript/reference/isimpleconnectionpoint-interface.md)\).  
  
## Vea también  
 [IDebugHelper \(Interfaz\)](../../winscript/reference/idebughelper-interface.md)   
 [ISimpleConnectionPoint \(Interfaz\)](../../winscript/reference/isimpleconnectionpoint-interface.md)