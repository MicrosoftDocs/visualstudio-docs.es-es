---
title: IDebugProgram3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3 interface
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ae6de25108cf93314db17a2ac8de9ce8b1dcaed2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148608"
---
# <a name="idebugprogram3"></a>IDebugProgram3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta interfaz representa un programa que se ejecuta en un proceso y extiende la [ejecución](../../../extensibility/debugger/reference/idebugprogram2-execute.md) proporcionando información de subprocesos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugProgram3 : IDebugProgram3  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (DE) y un proveedor de Puerto personalizado implementan esta interfaz para representar un programa en un proceso. El administrador de depuración de sesión (SDM) también implementa esta interfaz para proporcionar la información que se va a [adjuntar](../../../extensibility/debugger/reference/idebugprogram2-attach.md).  
  
## <a name="notes-for-callers"></a>Notas para llamadores  
 El evento [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) devuelve esta interfaz para un nuevo programa. Esta interfaz también se utiliza como parámetro para muchos métodos en varias interfaces.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 En la tabla siguiente se muestran los métodos de `IDebugProgram3` .  
  
|Método|Descripción|  
|------------|-----------------|  
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|Ejecuta el programa. El subproceso se devuelve para proporcionar a la información del depurador el subproceso que el usuario está viendo cuando se ejecuta.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Comentarios  
 Un programa es un contenedor de subprocesos que se ejecuta en una arquitectura en tiempo de ejecución determinada, mientras que un proceso se compone de uno o varios programas.  
  
## <a name="see-also"></a>Consulte también  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [Nueva](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [Ceso](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Incluir](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Ceso](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
