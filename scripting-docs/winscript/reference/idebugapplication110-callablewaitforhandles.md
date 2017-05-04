---
title: "IDebugApplication110::CallableWaitForHandles | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplication110::CallableWaitForHandles"
ms.assetid: 02e79b60-0d67-47f9-bf78-b65a02c9c014
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplication110::CallableWaitForHandles
Esperas para que identificadores especificados cualquiera de los se van al permitir que las llamadas entre subprocesos se envían a este subproceso.  Este método se debe llamar al subproceso del depurador.  
  
> [!IMPORTANT]
>  [IDebugApplication110 \(Interfaz\)](../../winscript/reference/idebugapplication110-interface.md) es implementado por PDM v11.0 y mayor.  Encontrado en activdbg100.h.  
  
## Sintaxis  
  
```cpp  
HRESULT CallableWaitForHandles([in] DWORD handleCount, [in, size_is(handleCount)] const HANDLE* pHandles, [out] DWORD* pIndex);  
  
```  
  
#### Parámetros  
 `handleCount`  
 El número de identificadores para esperar.  
  
 `pHandles`  
 El conjunto de identificadores para esperar.  
  
 `pIndex`  
 Cuando el valor de HRESULT es S\_OK, el índice en `pHandles` para el identificador que se notificó.  
  
## Vea también  
 [IDebugApplication110 \(Interfaz\)](../../winscript/reference/idebugapplication110-interface.md)