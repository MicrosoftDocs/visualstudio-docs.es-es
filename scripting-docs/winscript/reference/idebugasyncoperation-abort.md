---
title: "IDebugAsyncOperation::Abort | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugAsyncOperation.Abort
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugAsyncOperation::Abort"
ms.assetid: 232541c6-81b8-4eb7-96a7-a8e5fe087b31
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugAsyncOperation::Abort
Cancela una operación.  
  
## Sintaxis  
  
```  
HRESULT Abort();  
```  
  
#### Parámetros  
 Este método no toma ningún parámetro.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|S\_OK|El método se realizó correctamente.|  
|E\_NOTIMPL|Las operaciones no pueden cancelarse.|  
  
## Comentarios  
 Este método se llama normalmente en el subproceso del depurador para cancelar una operación no responde.  Este método hace que el método de `InProgressAbort` en el objeto de `IDebugSyncOperation` que se va a llamar.  
  
## Vea también  
 [IDebugAsyncOperation \(Interfaz\)](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)   
 [IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)