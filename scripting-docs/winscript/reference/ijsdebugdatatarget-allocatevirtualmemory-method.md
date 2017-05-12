---
title: "IJsDebugDataTarget::AllocateVirtualMemory (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.AllocateVirtualMemory
apilocation: jscript9diag.dll
ms.assetid: 1d3a77b0-c1de-4a0c-a759-3e0c68fd96dd
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::AllocateVirtualMemory (M&#233;todo)
Reserva y\/o confirma una región de memoria en el espacio de direcciones virtuales del proceso de destino.  
  
## Sintaxis  
  
```  
HRESULT AllocateVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD allocationType,  
   DWORD pageProtection,  
   UINT64 *pAllocatedAddress  
);  
```  
  
#### Parámetros  
 `address`  
 \[in\] Dirección dentro del proceso de destino donde se debe confirmar o reservar la memoria.  Este valor suele ser cero, en cuyo caso el sistema elige una dirección.  
  
 `size`  
 \[in\] El tamaño de la región de la memoria que se va a asignar en bytes.  El sistema redondea automáticamente hasta el límite de página siguiente.  
  
 `allocationType`  
 \[in\] Indica el tipo de asignación a realizar.  Normalmente es MEM\_COMMIT &#124; MEM\_RESERVE \(0x3000\), que reserva y confirma una asignación en un paso.  
  
 `pageProtection`  
 \[in\] La protección de memoria para la región de páginas que se va a asignar.  Si las páginas están confirmadas, puede especificar una de las constantes de la protección de memoria \(por ejemplo, PAGE\_READWRITE, PAGE\_EXECUTE\).  
  
 `pAllocatedAddress`  
 \[out\] Dirección base de la región de páginas asignada.  
  
## Valor devuelto  
  
## Comentarios  
 La función inicializa la memoria que asigna en cero, a menos que se utilice MEM\_RESET.  Para obtener más información, consulte la API VirtualAlloc de Win32.  
  
## Requisitos  
 **Encabezado:** jscript9diag.h  
  
## Vea también  
 [IJsDebugDataTarget \(Interfaz\)](../../winscript/reference/ijsdebugdatatarget-interface.md)