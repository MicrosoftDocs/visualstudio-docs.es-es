---
title: IDebugPortSupplier3 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortSupplier3
helpviewer_keywords: IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f0e1c5c252e0674ee3de8371080e298f42de2112
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
Esta interfaz permite que un autor de llamada determinar si un proveedor de puerto puede conservar los puertos (de escribirlos en disco) entre las distintas invocaciones del depurador y, a continuación, obtener una lista de esos puertos conservados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugPortSupplier3 : IDebugPortSupplier2  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un proveedor de puerto personalizado implementa esta interfaz para admitir conservar o guardar la información de puerto en el disco. Esta interfaz debe implementarse en el mismo objeto que la [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) interfaz.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Llame a [QueryInterface](/cpp/atl/queryinterface) en el `IDebugPortSupplier2` interfaz para obtener esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Además de los métodos heredados de la [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) interfaz, esta interfaz es compatible con lo siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Devuelve si el proveedor del puerto puede conservar puertos (de escribirlos en disco) entre las distintas invocaciones del depurador.|  
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Devuelve un objeto que puede utilizar para enumerar a través de todos los puertos que se escribieron en el disco por este proveedor del puerto.|  
  
## <a name="remarks"></a>Comentarios  
 Si un proveedor de puerto puede persistir puertos a través de invocaciones, deben implementar esta interfaz. Puertos deben cargarse cuando el proveedor del puerto se crea y se escriben en el disco cuando se destruye el proveedor del puerto.  
  
 Normalmente, un motor de depuración no interactúa con un proveedor de puerto y no tendrá ningún uso para esta interfaz.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)