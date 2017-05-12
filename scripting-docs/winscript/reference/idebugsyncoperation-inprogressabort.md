---
title: "IDebugSyncOperation::InProgressAbort | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugSyncOperation.InProgressAbort
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugSyncOperation::InProgressAbort"
ms.assetid: bfd0889c-b627-4843-b1c6-b6b918f42d61
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSyncOperation::InProgressAbort
Cancela una operación en curso en otro subproceso.  
  
## Sintaxis  
  
```  
HRESULT InProgressAbort();  
```  
  
#### Parámetros  
 Este método no toma ningún parámetro.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_NOTIMPL`|La operación no se puede cancelar.|  
|`E_ABORT`|No se puede completar la operación.|  
  
## Comentarios  
 El administrador de depuración llama a este método en el subproceso del depurador para cancelar una operación en curso en otro subproceso.  
  
 Si el método de `InProgressAbort` no puede completar la operación, devuelve `E_ABORT` lo más rápidamente posible.  Este método puede devolver `E_NOTIMPL` si la operación no se puede cancelar.  
  
## Vea también  
 [IDebugSyncOperation \(Interfaz\)](../../winscript/reference/idebugsyncoperation-interface.md)