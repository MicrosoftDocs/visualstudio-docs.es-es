---
title: "IJsDebugDataTarget (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: a9b784d6-958f-4d55-b3f6-c2d6b260a16b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget (Interfaz)
Implementado por el depurador para proporcionar funcionalidad para tener acceso y cambiar el estado del proceso del depurador de destino.  
  
## Sintaxis  
  
```  
IJsDebugDataTarget : public IUnknown;  
```  
  
## Members  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[IJsDebugDataTarget::AllocateVirtualMemory \(Método\)](../../winscript/reference/ijsdebugdatatarget-allocatevirtualmemory-method.md)|Reserva y\/o confirma una región de memoria en el espacio de direcciones virtuales del proceso de destino.|  
|[IJsDebugDataTarget::CreateStackFrameEnumerator \(Método\)](../../winscript/reference/ijsdebugdatatarget-createstackframeenumerator-method.md)|Crea un enumerador para los marcos de pila.|  
|[IJsDebugDataTarget::FreeVirtualMemory \(Método\)](../../winscript/reference/ijsdebugdatatarget-freevirtualmemory-method.md)|Libera y\/o anula una región de memoria en el espacio de direcciones virtuales del proceso de destino.|  
|[IJsDebugDataTarget::GetThreadContext \(Método\)](../../winscript/reference/ijsdebugdatatarget-getthreadcontext-method.md)|Recupera contexto para el subproceso especificado.|  
|[IJsDebugDataTarget::GetTlsValue \(Método\)](../../winscript/reference/ijsdebugdatatarget-gettlsvalue-method.md)|Para el subproceso que se está depurando, recupera el valor en la ranura del almacenamiento local de subprocesos \(TLS\) para el índice especificado de TLS.|  
|[IJsDebugDataTarget::ReadBSTR \(Método\)](../../winscript/reference/ijsdebugdatatarget-readbstr-method.md)|Lee BSTR del destino de depuración.|  
|[IJsDebugDataTarget::ReadMemory \(Método\)](../../winscript/reference/ijsdebugdatatarget-readmemory-method.md)|Lee la memoria del proceso de destino.|  
|[IJsDebugDataTarget::ReadNullTerminatedString \(Método\)](../../winscript/reference/ijsdebugdatatarget-readnullterminatedstring-method.md)|Lee el número especificado de caracteres del destino.|  
|[IJsDebugDataTarget::WriteMemory \(Método\)](../../winscript/reference/ijsdebugdatatarget-writememory-method.md)|Lee la memoria del proceso de destino.|  
  
## Requisitos  
 **Encabezado:** jscript9diag.h  
  
## Vea también  
 [Referencia de interfaces de Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)