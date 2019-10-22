---
title: Interfaz IJsDebugDataTarget | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a9b784d6-958f-4d55-b3f6-c2d6b260a16b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 85c77209230abfe261c9ec0b884ad0a677cfbf07
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572454"
---
# <a name="ijsdebugdatatarget-interface"></a>IJsDebugDataTarget (Interfaz)
Implementado por el depurador para proporcionar la funcionalidad para obtener acceso y cambiar el estado del proceso del depurador de destino.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
IJsDebugDataTarget : public IUnknown;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IJsDebugDataTarget::AllocateVirtualMemory (Método)](../../winscript/reference/ijsdebugdatatarget-allocatevirtualmemory-method.md)|Reserva o confirma una región de memoria en el espacio de direcciones virtuales del proceso de destino.|  
|[IJsDebugDataTarget::CreateStackFrameEnumerator (Método)](../../winscript/reference/ijsdebugdatatarget-createstackframeenumerator-method.md)|Crea un enumerador para los marcos de pila.|  
|[IJsDebugDataTarget::FreeVirtualMemory (Método)](../../winscript/reference/ijsdebugdatatarget-freevirtualmemory-method.md)|Libera o anula la confirmación de una región de memoria en el espacio de direcciones virtuales del proceso de destino.|  
|[IJsDebugDataTarget::GetThreadContext (Método)](../../winscript/reference/ijsdebugdatatarget-getthreadcontext-method.md)|Recupera el contexto del subproceso especificado.|  
|[IJsDebugDataTarget::GetTlsValue (Método)](../../winscript/reference/ijsdebugdatatarget-gettlsvalue-method.md)|Para el subproceso que se está depurando, recupera el valor de la ranura de almacenamiento local para el subproceso (TLS) para el índice TLS especificado.|  
|[IJsDebugDataTarget::ReadBSTR (Método)](../../winscript/reference/ijsdebugdatatarget-readbstr-method.md)|Lee un BSTR del destino de depuración.|  
|[IJsDebugDataTarget::ReadMemory (Método)](../../winscript/reference/ijsdebugdatatarget-readmemory-method.md)|Lee la memoria del proceso de destino.|  
|[IJsDebugDataTarget::ReadNullTerminatedString (Método)](../../winscript/reference/ijsdebugdatatarget-readnullterminatedstring-method.md)|Lee el número especificado de caracteres del destino.|  
|[IJsDebugDataTarget::WriteMemory (Método)](../../winscript/reference/ijsdebugdatatarget-writememory-method.md)|Lee la memoria del proceso de destino.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag. h  
  
## <a name="see-also"></a>Vea también  
 [Referencia de interfaces de Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)