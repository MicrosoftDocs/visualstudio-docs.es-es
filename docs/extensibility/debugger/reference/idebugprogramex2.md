---
title: IDebugProgramEx2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d8e26a21e00ff9f0fff664130171a302667ee414
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
Esta interfaz permite a la sesión de administrador de depuración (SDM) asociar a un programa y obtenga el nodo del programa asociado a un programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugProgramEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un proveedor de puerto personalizado implementa esta interfaz en el mismo objeto que la [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaz para permitir que el SDM asociar a un programa mientras al mismo tiempo, lo que permite el proveedor del puerto realizar el seguimiento de todas las sesiones adjunto a la programa. El proveedor del puerto personalizado puede implementar esta interfaz si así lo decide.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Las llamadas SDM [QueryInterface](/cpp/atl/queryinterface) en un `IDebugProgram2` interfaz para obtener esta interfaz para realizar un seguimiento de las sesiones que se han conectado a los programas.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugProgramEx2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Asociar](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Asocia un programa a una sesión.|  
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Obtiene el nodo de programa asociado a un programa.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz es privada entre el SDM y el programa.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)