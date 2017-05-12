---
title: "IDebugSyncOperation (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugSyncOperation (interfaz)"
ms.assetid: 8d714492-1836-462c-980a-c99e91a2c81b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSyncOperation (Interfaz)
Permite que un motor de script abstracto una operación \(como evaluación de la expresión\) que necesita realizarse mientras está anidado en un subproceso bloqueado determinado.  La interfaz también proporciona un mecanismo para cancelar operaciones insensibles.  
  
 Además de los métodos heredados de `IUnknown`, la interfaz `IDebugSyncOperation` expone los métodos siguientes.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)|Devuelve el subproceso de la aplicación de destino para esta operación síncrona.|  
|[IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)|Realiza sincrónicamente la operación y devuelve.|  
|[IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)|Cancela una operación en curso en otro subproceso.|