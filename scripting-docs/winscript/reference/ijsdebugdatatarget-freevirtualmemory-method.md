---
title: "IJsDebugDataTarget::FreeVirtualMemory (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.FreeVirtualMemory
apilocation: jscript9diag.dll
ms.assetid: ea54bad3-9ae3-436b-974d-70fc7fffefd6
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::FreeVirtualMemory (M&#233;todo)
Libera y\/o anula una región de memoria en el espacio de direcciones virtuales del proceso de destino.  
  
## Sintaxis  
  
```  
HRESULT FreeVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD freeType  
);  
```  
  
#### Parámetros  
 `address`  
 \[in\] Dirección dentro del proceso de destino donde se debe liberar la memoria.  
  
 `size`  
 \[in\] Número de bytes que se van a anular.  Para liberar un área de memoria, este valor debe ser cero.  
  
 `freeType`  
 \[in\] Indica el tipo de operación libre a realizar.  Suele ser MEM\_RELEASE \(0x8000\), que lanza el área de páginas especificada.  Después de la operación, las páginas quedan en el estado libre.  MEM\_DECOMMIT \(0x4000\) se puede utilizar en lugar de anular las páginas sin liberarlas.  
  
## Valor devuelto  
  
## Comentarios  
 Para obtener más información, consulte la API VirtualFree de Win32.  
  
## Requisitos  
 **Encabezado:** jscript9diag.h  
  
## Vea también  
 [IJsDebugDataTarget \(Interfaz\)](../../winscript/reference/ijsdebugdatatarget-interface.md)