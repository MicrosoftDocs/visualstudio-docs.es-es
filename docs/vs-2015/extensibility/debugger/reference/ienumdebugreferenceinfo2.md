---
title: IEnumDebugReferenceInfo2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2
helpviewer_keywords:
- IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 21c39c553a153707bad707d50cf5a13ae87973fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147751"
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta interfaz enumera [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) estructuras.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IEnumDebugReferenceInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (DE) implementa esta interfaz como parte de su compatibilidad con las referencias a los objetos de la memoria. Esta interfaz debe implementarse solo si se admiten referencias.  
  
## <a name="notes-for-callers"></a>Notas para llamadores  
 Visual Studio llama a [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) para obtener esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 En la tabla siguiente se muestran los métodos de `IEnumDebugReferenceInfo2` .  
  
|Método|Descripción|  
|------------|-----------------|  
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|Recupera un número especificado de estructuras [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) en una secuencia de enumeración.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|Omite un número especificado de estructuras de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) en la secuencia de enumeración.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|Restablece una secuencia de enumeración al principio.|  
|[Clonar](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|Obtiene el número de estructuras de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) en un enumerador.|  
  
## <a name="remarks"></a>Comentarios  
 Una referencia es esencialmente un tipo y una dirección, mientras que una propiedad es un nombre, un tipo y una dirección. Una referencia se mantiene siempre que el objeto al que se hace referencia existe en la memoria. Consulte [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) para obtener más información.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
