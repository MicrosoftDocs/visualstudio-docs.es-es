---
title: "ISimpleConnectionPoint (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "ISimpleConnectionPoint (interfaz)"
ms.assetid: f632a82f-942d-4291-963e-e9fa2b162493
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint (Interfaz)
Proporciona una manera sencilla para describir y enumerar los eventos desencadenados en un punto de conexión determinado.  Esta interfaz también facilita enlazar a un objeto de `IDispatch` a esos eventos.  Esta interfaz se implementa mediante el administrador de proceso \(PDM\) de depuración, y utilizada por los motores de scripts.  
  
 Esta interfaz está disponible de `IDebugHelper::CreateSimpleConnectionPoint`.  
  
 Además de los métodos heredados de `IUnknown`, la interfaz `ISimpleConnectionPoint` expone los métodos siguientes.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|Establece una conexión entre el objeto simple de punto de conexión y el receptor de cliente.|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|Devuelve el identificador de envío y el nombre de cada evento en un intervalo especificado de eventos.|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|Devuelve el número de eventos expuestos en esta interfaz.|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|Finaliza una conexión de consulta previamente establecida mediante `ISimpleConnectionPoint::Advise`.|  
  
## Vea también  
 [IDebugProperty \(Interfaz\)](../../winscript/reference/idebugproperty-interface.md)