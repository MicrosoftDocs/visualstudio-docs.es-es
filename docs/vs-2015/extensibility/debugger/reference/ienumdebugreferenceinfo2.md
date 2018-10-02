---
title: IEnumDebugReferenceInfo2 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugReferenceInfo2
helpviewer_keywords:
- IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 891022c12d3fe463c165653b5bf0b054efa751d5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576874"
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IEnumDebugReferenceInfo2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugreferenceinfo2).  
  
Esta interfaz enumera [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) estructuras.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IEnumDebugReferenceInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (DE) implementa esta interfaz como parte de su compatibilidad con las referencias a objetos en memoria. Esta interfaz se debe implementar solo si se admiten las referencias.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Llamadas visuales Studio [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) para obtener esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IEnumDebugReferenceInfo2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|Recupera un número especificado de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) estructuras en una secuencia de enumeración.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|Omite un número especificado de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) estructuras en la secuencia de enumeración.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|Restablece una secuencia de enumeración al principio.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|Obtiene el número de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) estructuras en un enumerador.|  
  
## <a name="remarks"></a>Comentarios  
 Una referencia es fundamentalmente un tipo y una dirección, mientras que una propiedad es un nombre, tipo y dirección. Una referencia persiste mientras conoce el objeto existe en memoria. Consulte [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) para obtener más detalles.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces del núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)

