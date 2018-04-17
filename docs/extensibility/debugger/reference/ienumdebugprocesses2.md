---
title: IEnumDebugProcesses2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugProcesses2
helpviewer_keywords:
- IEnumDebugProcesses2
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5fdc8d37700edb2776c905c45ddd97496228faf9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugprocesses2"></a>IEnumDebugProcesses2
Esta interfaz enumera los procesos que se ejecutan en un puerto de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IEnumDebugProcesses : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un proveedor de puerto personalizado implementa esta interfaz para proporcionar una lista de procesos que se ejecutan en un puerto.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Llamadas visuales Studio [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md) para obtener esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IEnumDebugProcesses2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|Recupera un número especificado de procesos en una secuencia de enumeración.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|Omite un número especificado de procesos en una secuencia de enumeración.|  
|[Restablecer](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|Restablece una secuencia de enumeración al principio.|  
|[clon](../../../extensibility/debugger/reference/ienumdebugprocesses2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|Obtiene el número de procesos de un enumerador.|  
  
## <a name="remarks"></a>Comentarios  
 Visual Studio usa esta interfaz para rellenar el **procesos** ventana.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)