---
title: "IDebugSessionProviderEx:StartDebugSession | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugSessionProviderEx:StartDebugSession
apilocation: scrobj.dll
ms.assetid: 247337ca-476c-4aa7-8500-d84fd1d98176
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugSessionProviderEx:StartDebugSession
Inicia una sesión de depuración con la aplicación especificada.  
  
## Sintaxis  
  
```  
HRESULT StartDebugSession(  
   IRemoteDebugApplication*  pda  
   BOOL  fQuery  
);  
```  
  
#### Parámetros  
 `pda`  
 \[in\] especifica la aplicación de depuración.  
  
 `fQuery`  
 \[in\] True indica una consulta.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método inicia una sesión de depuración con la aplicación especificada.  El depurador debe llamar a `IRemoteDebugApplication::ConnectDebugger` antes de volver de la llamada.  
  
## Vea también  
 [IDebugSessionProviderEx \(Interfaz\)](../../winscript/reference/idebugsessionproviderex-interface.md)   
 [IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)