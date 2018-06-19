---
title: IDebugProcessQueryProperties | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ac071afd9f9ce7d45a05408aeec32117776832f2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31116196"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
Esta interfaz es una interfaz de extensión implementada por [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) los implementadores. Permite el implementador obtener información sobre el entorno del proceso de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugProcessQueryProperties: IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Implemente esta interfaz para obtener información sobre el entorno de ejecución de un proceso de depuración.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugProcessQueryProperties`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Busca un valor de propiedad.|  
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Consultas para los valores de propiedad.|  
  
## <a name="remarks"></a>Comentarios  
 Rara vez se implementa esta interfaz.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)