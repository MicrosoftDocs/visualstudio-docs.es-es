---
title: "IDebugApplication::FireDebuggerEvent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.FireDebuggerEvent
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::FireDebuggerEvent"
ms.assetid: fd1f602e-fc15-4158-a6e7-497ff5b4a509
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::FireDebuggerEvent
Desencadena un evento genérico a la interfaz de `IApplicationDebugger` del depurador.  
  
## Sintaxis  
  
```  
HRESULT FireDebuggerEvent(  
   REFGUID    riid,  
   IUnknown*  punk  
);  
```  
  
#### Parámetros  
 `riid`  
 \[in\] GUID para el objeto.  
  
 `punk`  
 \[in\] un objeto de evento al paso en el depurador.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_NOTIMPL`|No se implementa el método actualmente.|  
  
## Comentarios  
 La semántica de GUID y `IUnknown` son totalmente application\/depurador definido.  
  
 Este método permite las expansiones de modelo de depurador; no se implementa actualmente.  
  
 Este método hace que `IApplicationDebugger::onDebuggerEvent` que se va a llamar.  
  
## Vea también  
 [IDebugApplication \(Interfaz\)](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onDebuggerEvent](../../winscript/reference/iapplicationdebugger-ondebuggerevent.md)