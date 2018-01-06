---
title: IDebugProgram3 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugProgram3 interface
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: cb827c875731134b9d8f9ea2833f3629ca0d3c36
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram3"></a>IDebugProgram3
Esta interfaz representa un programa que se ejecuta en un proceso y extiende [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md) proporcionando información del subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugProgram3 : IDebugProgram3  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (Alemania) y un proveedor de puerto personalizado implementan esta interfaz para representar un programa en un proceso. El Administrador de sesión de depuración (SDM) también implementa esta interfaz para proporcionar información a [adjuntar](../../../extensibility/debugger/reference/idebugprogram2-attach.md).  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 El [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) evento devuelve esta interfaz para un nuevo programa. Esta interfaz también se utiliza como un parámetro para muchos métodos en varias interfaces.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugProgram3`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|Ejecuta el programa. El subproceso se devuelve para proporcionar a la información del depurador de subproceso en el que el usuario ve cuando se ejecuta.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Comentarios  
 Un programa es un contenedor de subproceso que se ejecuta en una determinada arquitectura de tiempo de ejecución, mientras que un proceso se compone de uno o más programas.  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [Siguiente](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)