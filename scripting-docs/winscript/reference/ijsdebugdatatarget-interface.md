---
title: IJsDebugDataTarget (interfaz) | Documentos de Microsoft
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
ms.openlocfilehash: 94e158ced0da6d59bfcadeb87bf206c94a6099ad
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729285"
---
# <a name="ijsdebugdatatarget-interface"></a>IJsDebugDataTarget (Interfaz)
Implementa el depurador para proporcionar la funcionalidad necesaria para tener acceso y cambiar el estado del proceso del depurador de destino.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IJsDebugDataTarget : public IUnknown;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IJsDebugDataTarget::AllocateVirtualMemory (Método)](../../winscript/reference/ijsdebugdatatarget-allocatevirtualmemory-method.md)|Reserva o confirma una región de memoria en el espacio de direcciones virtuales del proceso de destino.|  
|[IJsDebugDataTarget::CreateStackFrameEnumerator (Método)](../../winscript/reference/ijsdebugdatatarget-createstackframeenumerator-method.md)|Crea un enumerador para los marcos de pila.|  
|[IJsDebugDataTarget::FreeVirtualMemory (Método)](../../winscript/reference/ijsdebugdatatarget-freevirtualmemory-method.md)|Libera o anula el registro de una región de memoria en el espacio de direcciones virtuales del proceso de destino.|  
|[IJsDebugDataTarget::GetThreadContext (Método)](../../winscript/reference/ijsdebugdatatarget-getthreadcontext-method.md)|Contexto de recupera para tiene subprocesos.|  
|[IJsDebugDataTarget::GetTlsValue (Método)](../../winscript/reference/ijsdebugdatatarget-gettlsvalue-method.md)|Para el subproceso que se está depurando, recupera el valor de la ranura de almacenamiento local (TLS) del subproceso para el índice especificado de TLS.|  
|[IJsDebugDataTarget::ReadBSTR (Método)](../../winscript/reference/ijsdebugdatatarget-readbstr-method.md)|Lee una cadena BSTR desde el destino de depuración.|  
|[IJsDebugDataTarget::ReadMemory (Método)](../../winscript/reference/ijsdebugdatatarget-readmemory-method.md)|Lee la memoria del proceso de destino.|  
|[IJsDebugDataTarget::ReadNullTerminatedString (Método)](../../winscript/reference/ijsdebugdatatarget-readnullterminatedstring-method.md)|Lee el número especificado de caracteres desde el destino.|  
|[IJsDebugDataTarget::WriteMemory (Método)](../../winscript/reference/ijsdebugdatatarget-writememory-method.md)|Lee la memoria del proceso de destino.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia de interfaces de Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)