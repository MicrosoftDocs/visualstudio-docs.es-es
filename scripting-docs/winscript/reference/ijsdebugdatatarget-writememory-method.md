---
title: "IJsDebugDataTarget::WriteMemory (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.WriteMemory
apilocation: jscript9diag.dll
ms.assetid: 0d3c04c3-9ef8-4842-a145-3d29bca75062
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::WriteMemory (M&#233;todo)
Lee la memoria del proceso de destino.  
  
## Sintaxis  
  
```  
HRESULT WriteMemory(  
   UINT64 address,  
   const BYTE *pMemory,  
   DWORD size  
);  
```  
  
#### Parámetros  
 `address`  
 \[in\] Dirección base en la que escribir la memoria del proceso de destino.  
  
 `pMemory`  
 \[in\] Los datos a escribir en el espacio de direcciones de proceso especificado.  
  
 `size`  
 \[in\] Número de bytes que se van a escribir en el proceso.  
  
## Valor devuelto  
  
## Comentarios  
 Antes de que se produzca la transferencia de datos, el sistema comprueba que se puede tener acceso de escritura a todos los datos de la dirección base y a la memoria del tamaño especificado y, si no es así, la función produce un error E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS.  
  
## Requisitos  
 **Encabezado:** jscript9diag.h  
  
## Vea también  
 [IJsDebugDataTarget \(Interfaz\)](../../winscript/reference/ijsdebugdatatarget-interface.md)