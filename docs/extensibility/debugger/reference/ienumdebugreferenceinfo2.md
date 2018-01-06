---
title: IEnumDebugReferenceInfo2 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugReferenceInfo2
helpviewer_keywords: IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9c7bcba4207e5caa14b9db27f2d9b243376c6d01
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
Esta interfaz enumera [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) estructuras.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IEnumDebugReferenceInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (Alemania) implementa esta interfaz como parte de su compatibilidad con las referencias a objetos en memoria. Esta interfaz se debe implementar únicamente si se admiten referencias.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Llamadas visuales Studio [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) para obtener esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IEnumDebugReferenceInfo2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|Recupera un número especificado de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) estructuras en una secuencia de enumeración.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|Omite un número especificado de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) estructuras en la secuencia de enumeración.|  
|[Restablecer](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|Restablece una secuencia de enumeración al principio.|  
|[Clon](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|Obtiene el número de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) estructuras en un enumerador.|  
  
## <a name="remarks"></a>Comentarios  
 Una referencia es básicamente un tipo y una dirección, mientras que una propiedad es un nombre, tipo y dirección. Se mantiene una referencia como referencia de objeto existe en la memoria. Vea [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) para obtener más detalles.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)