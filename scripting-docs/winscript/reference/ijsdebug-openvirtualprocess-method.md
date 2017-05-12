---
title: "IJsDebug::OpenVirtualProcess (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJSDebug.OpenVirtualProcess
apilocation: jscript9diag.dll
ms.assetid: 5612bf1b-a4e3-4eaf-ac5e-c2e1f147c395
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebug::OpenVirtualProcess (M&#233;todo)
Método de generador utilizado para crear un nuevo objeto de proceso virtual.  
  
## Sintaxis  
  
```  
 HRESULT OpenVirtualProcess(  
   DWORD processId,  
   UINT64 runtimeJsBaseAddress,  
   IJsDebugDataTarget *pDataTarget,  
   IJsDebugProcess **ppProcess  
);  
```  
  
#### Parámetros  
 `processId`  
 \[in\] Identificador de proceso al que asociar el depurador.  
  
 `runtimeJsBaseAddress`  
 \[in\] Dirección base donde se ha cargado el runtime JavaScript en el proceso de destino.  
  
 `pDataTarget`  
 \[in\] Interfaz proporcionada por el depurador para consultar el estado del proceso.  
  
 `ppProcess`  
 \[out\] Nuevo objeto de proceso de depuración  
  
## Valor devuelto  
  
## Comentarios  
 Devuelve E\_JsDEBUG\_MISMATCHED\_RUNTIME si no coinciden Jscript9diag y Jscript9.  
  
## Requisitos  
 **Encabezado:** jscript9diag.h  
  
## Vea también  
 [IJsDebug \(Interfaz\)](../../winscript/reference/ijsdebug-interface.md)