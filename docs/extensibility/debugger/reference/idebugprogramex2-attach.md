---
title: IDebugProgramEx2::Attach | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: c58f576a0126472ad60ceeb5fc5289b668bd54dd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
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
 [in] Un [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objeto que representa la función de devolución de llamada que el motor de depuración adjunto envía eventos a.  
  
 `dwReason`  
 [in] Un valor de la [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) enumeración que describe el motivo de la operación de adjuntar.  
  
 `pSession`  
 [in] Un valor que identifica de forma única la sesión que se está asociando al programa.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error. Este método debe devolver `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` si el programa ya está conectado.  
  
## <a name="remarks"></a>Comentarios  
 El puerto que contiene el programa puede usar el valor de `pSession` para determinar qué sesión está intentando conectarse al programa. Por ejemplo, si un puerto permite la sesión de solo depuración para asociar a un proceso a la vez, el puerto puede determinar si la misma sesión ya está conectada a otros programas en el proceso.  
  
> [!NOTE]
>  La interfaz se pasa en `pSession` debe tratarse como una cookie, un valor que identifica de forma única el Administrador de sesión de depuración asociar a este programa; ninguno de los métodos de la interfaz proporcionada es funcional.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)