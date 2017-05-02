---
title: "IDebugApplicationNode100 (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNode100 (Interfaz)"
ms.assetid: 43966d4e-5f89-4a04-a08d-782347d00c2d
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugApplicationNode100 (Interfaz)
La interfaz de `IDebugApplicationNode100` extiende la funcionalidad de [IDebugApplicationNode \(Interfaz\)](../../winscript/reference/idebugapplicationnode-interface.md).  Puede obtener una instancia de esta interfaz llamando a QueryInterface en una implementación de [IDebugApplicationNode \(Interfaz\)](../../winscript/reference/idebugapplicationnode-interface.md).  
  
> [!IMPORTANT]
>  Esta interfaz se implementa por PDM v10.0 y mayor.  Encontrado en activdbg100.h.  
  
## Métodos  
 La interfaz `IDebugApplicationNode100` expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md)|Obtiene los documentos de texto que son ocultados por el filtro especificado.|  
|[IDebugApplicationNode100::QueryIsChildNode](../../winscript/reference/idebugapplicationnode100-queryischildnode.md)|Determina si el documento especificado pertenece a uno de los nodos secundarios de este nodo.|  
|[IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)|Establece el filtro en una implementación concreta de [IDebugApplicationNodeEvents \(Interfaz\)](../../winscript/reference/idebugapplicationnodeevents-interface.md) .  Permite que los depuradores del archivo de comandos filtren nodos secundarios out compilador\- generados de la aplicación para que el PDM envíe no más eventos cuando se crean o se quitan los nodos.  De forma predeterminada, todos los nodos se enviará.|