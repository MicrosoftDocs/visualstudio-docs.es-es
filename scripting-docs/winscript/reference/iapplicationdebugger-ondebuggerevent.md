---
title: "IApplicationDebugger::onDebuggerEvent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebugger.onDebuggerEvent
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebugger::onDebuggerEvent"
ms.assetid: 82a5faaa-1222-4bf1-8569-10439dbdf16d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebugger::onDebuggerEvent
Controla un evento de aplicación personalizado.  
  
## Sintaxis  
  
```  
HRESULT onDebuggerEvent(  
   REFIID     riid,  
   IUnknown*  punk  
);  
```  
  
#### Parámetros  
 `riid`  
 \[in\] identificador de interfaz para obtener el objeto.  
  
 `punk`  
 \[in\] el objeto de evento de Bytes, que implementa la interfaz definida por `riid`.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_NOTIMPL`|No se implementa el método actualmente.|  
  
## Comentarios  
 La semántica de `IUnknown` es totalmente application\/depurador definido.  
  
 Este método permite las expansiones de modelo de depurador; no se implementa actualmente.  
  
 Se llama a este método cuando se llama a `IDebugApplication::FireDebuggerEvent` .  
  
## Vea también  
 [IApplicationDebugger \(Interfaz\)](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)