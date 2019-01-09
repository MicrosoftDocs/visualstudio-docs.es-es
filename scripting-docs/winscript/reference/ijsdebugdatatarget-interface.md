---
title: IJsDebugDataTarget (interfaz) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a9b784d6-958f-4d55-b3f6-c2d6b260a16b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e14046443ca0560deacb6ddb6e39b1fc25d18fea
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097427"
---
# <a name="ijsdebugdatatarget-interface"></a>IJsDebugDataTarget (Interfaz)
Implementado por el depurador para proporcionar funcionalidad para obtener acceso y cambiar el estado del proceso del depurador de destino.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
IJsDebugDataTarget : public IUnknown;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IJsDebugDataTarget::AllocateVirtualMemory (Método)](../../winscript/reference/ijsdebugdatatarget-allocatevirtualmemory-method.md)|Reserva y/o confirma una región de memoria en el espacio de direcciones virtuales del proceso de destino.|  
|[IJsDebugDataTarget::CreateStackFrameEnumerator (Método)](../../winscript/reference/ijsdebugdatatarget-createstackframeenumerator-method.md)|Crea un enumerador para marcos de pila.|  
|[IJsDebugDataTarget::FreeVirtualMemory (Método)](../../winscript/reference/ijsdebugdatatarget-freevirtualmemory-method.md)|Libera y/o anula una región de memoria en el espacio de direcciones virtuales del proceso de destino.|  
|[IJsDebugDataTarget::GetThreadContext (Método)](../../winscript/reference/ijsdebugdatatarget-getthreadcontext-method.md)|Recupera contexto para el subproceso especificado.|  
|[IJsDebugDataTarget::GetTlsValue (Método)](../../winscript/reference/ijsdebugdatatarget-gettlsvalue-method.md)|Para el subproceso que se está depurando, recupera el valor en la ranura de subproceso (TLS) de almacenamiento local para el índice especificado de TLS.|  
|[IJsDebugDataTarget::ReadBSTR (Método)](../../winscript/reference/ijsdebugdatatarget-readbstr-method.md)|Lee BSTR del destino de depuración.|  
|[IJsDebugDataTarget::ReadMemory (Método)](../../winscript/reference/ijsdebugdatatarget-readmemory-method.md)|Lee la memoria del proceso de destino.|  
|[IJsDebugDataTarget::ReadNullTerminatedString (Método)](../../winscript/reference/ijsdebugdatatarget-readnullterminatedstring-method.md)|Lee el número especificado de caracteres desde el destino.|  
|[IJsDebugDataTarget::WriteMemory (Método)](../../winscript/reference/ijsdebugdatatarget-writememory-method.md)|Lee la memoria del proceso de destino.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia de interfaces de Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)