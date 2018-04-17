---
title: IEnumCodePaths2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fc2441d2257c5e3c3e6d205ea27b64e03938490b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
Esta interfaz representa una lista de las rutas de código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IEnumCodePaths2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (Alemania) implementa esta interfaz para representar una lista de las rutas de código.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Llame a [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) para obtener esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IEnumCodePaths2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Siguiente](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|Recupera un número especificado de las rutas de código en una secuencia de enumeración.|  
|[Skip](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|Omite un número especificado de las rutas de código en una secuencia de enumeración.|  
|[Restablecer](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|Restablece una secuencia de enumeración al principio.|  
|[clon](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|Obtiene el número de rutas de acceso de código de un enumerador.|  
  
## <a name="remarks"></a>Comentarios  
 Una ruta de acceso de código representa una llamada de función o el punto de bifurcación en un programa. Una lista de las rutas de código representa la ruta de acceso a través del cual se ha tomado la ejecución del código.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)