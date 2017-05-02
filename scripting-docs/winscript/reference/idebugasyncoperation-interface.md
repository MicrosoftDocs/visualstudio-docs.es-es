---
title: "IDebugAsyncOperation (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugAsyncOperation (interfaz)"
ms.assetid: ebb2ea75-1443-4d8a-812d-171a166f5f9d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugAsyncOperation (Interfaz)
El administrador de la depuración implementa la interfaz de `IDebugAsyncOperation` .  Un motor de lenguaje llama al método de `IDebugApplication::CreateAsyncDebugOperation` para obtener una referencia a esta interfaz.  El motor de lenguaje puede utilizar la interfaz de `IDebugAsyncOperation` para proporcionar acceso asincrónico a una operación sincrónica de depuración.  
  
 Además de los métodos heredados de `IUnknown`, la interfaz `IDebugAsyncOperation` expone los métodos siguientes.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugAsyncOperation::GetSyncDebugOperation](../../winscript/reference/idebugasyncoperation-getsyncdebugoperation.md)|Devuelve la operación sincrónica de depuración asociada a este objeto.|  
|[IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)|Hace que la operación asincrónica a start.|  
|[IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)|Cancela una operación.|  
|[IDebugAsyncOperation::QueryIsComplete](../../winscript/reference/idebugasyncoperation-queryiscomplete.md)|Determina si la operación de depuración ha finalizado.|  
|[IDebugAsyncOperation::GetResult](../../winscript/reference/idebugasyncoperation-getresult.md)|Proporciona el valor devuelto y devuelve parámetro de objeto de la operación sincrónica de depuración.|