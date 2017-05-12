---
title: "IJsDebugDataTarget::ReadMemory (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.ReadMemory
apilocation: jscript9diag.dll
ms.assetid: 664e0f7d-2007-45f4-b993-36fe8b1944e5
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::ReadMemory (M&#233;todo)
Lee la memoria del proceso de destino.  
  
## Sintaxis  
  
```  
HRESULT ReadMemory(  
   UINT64 address,  
   JsDebugReadMemoryFlags flags,  
   BYTE *pBuffer,  
   DWORD size,  
   DWORD *pBytesRead  
);  
```  
  
#### Parámetros  
 `address`  
 \[in\] Dirección base de la que leer la memoria del proceso de destino.  
  
 `flags`  
 \[in\] Marcas que controlan el comportamiento de ReadMemory.  
  
 `pBuffer`  
 \[out\] Búfer de Proyecto que recibe el contenido del espacio de direcciones del proceso de destino.  Si hay error, el contenido de este búfer no está especificado.  
  
 `size`  
 \[in\] Número máximo de bytes que se van a leer del proceso.  
  
 `pBytesRead`  
 \[out\] Indica el número de bytes leídos realmente del proceso de destino.  Si JsDebugAllowPartialRead está desactivado, si se realiza correctamente, este valor siempre será exactamente igual al tamaño de entrada.  Si JsDebugAllowPartialRead está especificado, si se realiza correctamente, este valor es mayor que cero.  
  
## Valor devuelto  
  
## Comentarios  
 Devuelve S\_OK si se realiza correctamente y se usan códigos de error para cualquier error.  Devuelve E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS si la dirección no es válida.  Para obtener más información, vea JsDebugAllowPartialRead.  
  
## Requisitos  
 **Encabezado:** jscript9diag.h  
  
## Vea también  
 [IJsDebugDataTarget \(Interfaz\)](../../winscript/reference/ijsdebugdatatarget-interface.md)