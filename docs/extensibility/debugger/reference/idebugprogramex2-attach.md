---
title: IDebugProgramEx2::Attach | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f885bd3cdd09caa145451e922ad154b60fdb1ff4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53900592"
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
Asociar una sesión de un programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason,  
   IDebugSession2*       pSession  
);  
```  
  
```  
[C#]  
int Attach(   
   IDebugEventCallback2 pCallback,  
   uint                 dwReason,  
   IDebugSession2       pSession  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pCallback`  
 [in] Un [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objeto que representa la función de devolución de llamada que el motor de depuración adjuntos envía eventos a.  
  
 `dwReason`  
 [in] Un valor de la [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) enumeración que describe el motivo de la operación de adjuntar.  
  
 `pSession`  
 [in] Un valor que identifica de forma única la sesión que se está asociando al programa.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. Este método debe devolver `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` si el programa ya está asociado.  
  
## <a name="remarks"></a>Comentarios  
 El puerto que contiene el programa puede usar el valor de `pSession` para determinar qué sesión está intentando adjuntar al programa. Por ejemplo, si un puerto permite la sesión de solo depuración adjuntar a un proceso a la vez, el puerto puede determinar si la misma sesión ya está conectada a otros programas en el proceso.  
  
> [!NOTE]
>  La interfaz pasa `pSession` se trata solo como una cookie, un valor que identifica el Administrador de depuración de la sesión asociar a este programa; ninguno de los métodos en la interfaz proporcionado son funcional.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)