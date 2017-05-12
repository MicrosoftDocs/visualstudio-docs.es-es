---
title: "IDebugApplicationNode100::SetFilterForEventSink | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNode100::SetFilterForEventSink"
ms.assetid: cfb34efe-c6e1-4692-8ffd-3ede3a24cd4b
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugApplicationNode100::SetFilterForEventSink
Establece el filtro en una implementación concreta de [IDebugApplicationNodeEvents \(Interfaz\)](../../winscript/reference/idebugapplicationnodeevents-interface.md) .  Permite que los depuradores del archivo de comandos filtren nodos secundarios out compilador\- generados de la aplicación para que el PDM envíe no más eventos cuando se crean o se quitan estos.  De forma predeterminada, todos los nodos se enviará.  
  
> [!IMPORTANT]
>  [IDebugApplicationNode100 \(Interfaz\)](../../winscript/reference/idebugapplicationnode100-interface.md) es implementado por PDM v10.0 y mayor.  Encontrado en activdbg100.h.  
  
## Sintaxis  
  
```cpp  
HRESULT SetFilterForEventSink(  
        [in] DWORD dwCookie,  
        [in] APPLICATION_NODE_EVENT_FILTER filter  
        );  
  
```  
  
#### Parámetros  
 `dwCookie`  
 La cookie del filtro.  
  
 `filter`  
 El filtro.  
  
## Vea también  
 [IDebugApplicationNode100 \(Interfaz\)](../../winscript/reference/idebugapplicationnode100-interface.md)