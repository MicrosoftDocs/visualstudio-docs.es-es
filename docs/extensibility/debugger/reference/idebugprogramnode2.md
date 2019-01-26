---
title: IDebugProgramNode2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2
helpviewer_keywords:
- IDebugProgramNode2 interface
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de17039a10137ba6fb0075b9943d0771eb166e33
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54981108"
---
# <a name="idebugprogramnode2"></a>IDebugProgramNode2
Esta interfaz representa un programa que se puede depurar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugProgramNode2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un motor de depuración (DE) o un proveedor de puerto personalizado implementa esta interfaz para representar un programa que se puede depurar. Esta interfaz se implementa normalmente en el mismo objeto que implementa el [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaz. Esta interfaz se registra con [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] mediante una llamada a [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Llame a [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) para devolver esta interfaz. Un proveedor de puerto personalizado recibe esta interfaz mediante una llamada a [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). A DE recibe esta interfaz mediante una llamada a [adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugProgramNode2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|Obtiene el nombre de un programa.|  
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|Obtiene el nombre del proceso que hospeda un programa.|  
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|Obtiene el identificador de proceso del sistema para el proceso de hospedaje de un programa.|  
|[GetHostMachineName_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|EN DESUSO. NO USE.|  
|[Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|EN DESUSO. NO USE. Consulte la [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interfaz para un enfoque alternativo.|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|Obtiene el nombre y el identificador de la DE ejecutar este programa.|  
|[DetachDebugger_V7](../../../extensibility/debugger/reference/idebugprogramnode2-detachdebugger-v7.md)|EN DESUSO. NO USE.|  
  
## <a name="remarks"></a>Comentarios  
 El Administrador de depuración de la sesión (SDM) llama normalmente [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) para obtener esta interfaz.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Msdbg.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces del núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)   
 [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)   
 [Adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)   
 [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)