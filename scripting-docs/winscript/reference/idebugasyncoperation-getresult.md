---
title: "IDebugAsyncOperation::GetResult | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugAsyncOperation.GetResult
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugAsyncOperation::GetResult"
ms.assetid: 56d43365-6b12-4213-a97c-953c40d7b7f6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugAsyncOperation::GetResult
Proporciona el valor devuelto y devuelve parámetro de objeto de la operación sincrónica de depuración.  
  
## Sintaxis  
  
```  
HRESULT GetResult(  
   HRESULT*    phrResult,  
   IUnknown**  ppunkResult  
);  
```  
  
#### Parámetros  
 `phrResult`  
 \[out\] si se completa la operación, `phrResult` es el valor devuelto de `IDebugSyncOperation::Execute`.  
  
 `ppunkResult`  
 \[out\] si se completa la operación, `ppunkResult` es el parámetro de objeto devuelto por la operación.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_PENDING`|La operación no ha finalizado.|  
  
## Comentarios  
 Si la operación se ha completado, retornos de este método `HRESULT` y el parámetro de objeto de `IDebugSyncOperation::Execute`.  
  
## Vea también  
 [IDebugAsyncOperation \(Interfaz\)](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)