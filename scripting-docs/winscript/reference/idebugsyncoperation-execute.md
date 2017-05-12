---
title: "IDebugSyncOperation::Execute | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugSyncOperation.Execute
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugSyncOperation::Execute"
ms.assetid: a45b8c7d-c51a-4098-877f-fbec2f1f6947
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSyncOperation::Execute
Realiza sincrónicamente la operación y devuelve.  
  
## Sintaxis  
  
```  
HRESULT Execute(  
   IUnknown**  ppunkResult  
);  
```  
  
#### Parámetros  
 `ppunkResult`  
 \[out\] parámetro del objeto Se devuelto por la operación.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_ABORT`|La operación se anuló llamando al método de `IDebugSyncOperation::InProgressAbort` .|  
  
## Comentarios  
 El administrador de la depuración en el subproceso de destino llama al método de `Execute` sincrónicamente.  
  
## Vea también  
 [IDebugSyncOperation \(Interfaz\)](../../winscript/reference/idebugsyncoperation-interface.md)