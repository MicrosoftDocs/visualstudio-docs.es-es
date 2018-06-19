---
title: IDebugEngine2::Attach | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 264ef65472bf3d003852f2f7efc0fe21ee45d2a1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107925"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
Asocia un motor de depuración (Alemania) a un programa o programas. Llamado por el Administrador de sesión de depuración (SDM) cuando el Alemania se está ejecutando en proceso para el SDM.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Attach(   
   IDebugProgram2**      pProgram,  
   IDebugProgramNode2**  rgpProgramNodes,  
   DWORD                 celtPrograms,  
   IDebugEventCallback2* pCallback,  
   ATTACH_REASON         dwReason  
);  
```  
  
```csharp  
int Attach(   
   IDebugProgram2[]     pProgram,  
   IDebugProgramNode2[] rgpProgramNodes,  
   uint                 celtPrograms,  
   IDebugEventCallback2 pCallback,  
   Enum_ATTACH_REASON   dwReason  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pProgram`  
 [in] Una matriz de [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objetos que representan los programas que se adjuntará a. Se trata de programas de puerto.  
  
 `rgpProgramNodes`  
 [in] Una matriz de [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objetos que representan los nodos de programa, uno por cada programa. Los nodos de programa en esta matriz representan los mismos programas como en `pProgram`. Los nodos de programa se proporcionan para que la DE puede identificar los programas para adjuntar a.  
  
 `celtPrograms`  
 [in] Número de programas o nodos de programa en el `pProgram` y `rgpProgramNodes` matrices.  
  
 `pCallback`  
 [in] El [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objeto que se usará para enviar eventos de depuración para el SDM.  
  
 `dwReason`  
 [in] Un valor de la [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) enumeración que especifica la razón para asociar estos programas. Para obtener más información, vea la sección Comentarios.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Hay tres razones para asociarse a un programa, como se indica a continuación:  
  
-   `ATTACH_REASON_LAUNCH` indica que se está asociando el Alemania al programa porque el usuario inicia el proceso que lo contiene.  
  
-   `ATTACH_REASON_USER` indica que el usuario ha solicitado explícitamente la DE para adjuntar a un programa (o el proceso que contiene un programa).  
  
-   `ATTACH_REASON_AUTO` indica que se está asociando el Alemania a un programa en particular porque está realizando la depuración de otros programas en un proceso determinado. También se denomina asociación automática.  
  
 Cuando se llama a este método, la DE necesita enviar estos eventos en secuencia:  
  
1.  [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (si todavía no se ha enviado a una instancia determinada del motor de depuración)  
  
2.  [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
3.  [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)  
  
 Además, si es el motivo para adjuntar `ATTACH_REASON_LAUNCH`, debe enviar la DE la [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) eventos.  
  
 Una vez los obtiene DE la [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objeto correspondiente al programa que se está depurando, se puede consultar para cualquier interfaz privada.  
  
 Antes de llamar a los métodos de un nodo de programa en la matriz proporcionada por `pProgram` o `rgpProgramNodes`, suplantación, si es necesario, debe estar habilitada en el `IDebugProgram2` interfaz que representa el nodo de programa. Normalmente, sin embargo, este paso no es necesario. Para obtener más información, consulte [problemas de seguridad](../../../extensibility/debugger/security-issues.md).  
  
## <a name="see-also"></a>Vea también  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)