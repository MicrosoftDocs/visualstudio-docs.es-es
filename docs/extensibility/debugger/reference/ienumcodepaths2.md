---
title: IEnumCodePaths2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 20bfd418da802e136fd92948285f9431efae88ad
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54982122"
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
Esta interfaz representa una lista de rutas de acceso del código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IEnumCodePaths2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (DE) implementa esta interfaz para representar una lista de rutas de acceso del código.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Llame a [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) para obtener esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IEnumCodePaths2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Siguiente](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|Recupera un número especificado de las rutas de código en una secuencia de enumeración.|  
|[Skip](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|Omite un número especificado de las rutas de código en una secuencia de enumeración.|  
|[Reset](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|Restablece una secuencia de enumeración al principio.|  
|[Clone](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|Obtiene el número de rutas de acceso del código en un enumerador.|  
  
## <a name="remarks"></a>Comentarios  
 Una ruta de acceso del código representa una llamada de función o el punto de rama en un programa. Una lista de las rutas de código representa la ruta de acceso a través del cual se ha tomado la ejecución del código.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)