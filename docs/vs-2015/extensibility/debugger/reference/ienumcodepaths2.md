---
title: IEnumCodePaths2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 577b2691ed67751407621d5000ee9a8abec318df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192014"
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta interfaz representa una lista de rutas de acceso de código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IEnumCodePaths2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor DE depuración (DE) implementa esta interfaz para representar una lista de rutas de acceso de código.  
  
## <a name="notes-for-callers"></a>Notas para llamadores  
 Llame a [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) para obtener esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 En la tabla siguiente se muestran los métodos de `IEnumCodePaths2` .  
  
|Método|Descripción|  
|------------|-----------------|  
|[Siguiente](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|Recupera un número especificado de rutas de acceso de código en una secuencia de enumeración.|  
|[Skip](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|Omite un número especificado de rutas de acceso de código en una secuencia de enumeración.|  
|[Reset](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|Restablece una secuencia de enumeración al principio.|  
|[Clonar](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|Obtiene el número de rutas de acceso de código en un enumerador.|  
  
## <a name="remarks"></a>Comentarios  
 Una ruta de acceso de código representa una llamada de función o punto de bifurcación en un programa. Una lista de rutas de código representa la ruta de acceso en la que se ha realizado la ejecución del código.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
