---
title: IEnumDebugErrorBreakpoints2 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugErrorBreakpoints2
helpviewer_keywords: IEnumDebugErrorBreakpoints2
ms.assetid: ffdad73d-969a-45ef-9ad1-7f5d3b814018
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3ecef99eaafcd85c2318d2515a71c849fa8de2e2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugerrorbreakpoints2"></a>IEnumDebugErrorBreakpoints2
Esta interfaz enumera los puntos de interrupción de error asociados a un punto de interrupción pendiente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IEnumDebugErrorBreakpoints2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (Alemania) implementa esta interfaz como parte de su compatibilidad con los puntos de interrupción.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Llamadas visuales Studio [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) para obtener esta interfaz que representa una lista de puntos de interrupción que no se puede enlazar, o [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) para obtener esta interfaz que representa una lista de puntos de interrupción que no se han enlazado.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IEnumDebugErrorBreakpoints2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)|Recupera un número especificado de los puntos de interrupción de error en una secuencia de enumeración.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-skip.md)|Omite un número especificado de puntos de interrupción de error en una secuencia de enumeración.|  
|[Restablecer](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-reset.md)|Restablece una secuencia de enumeración al principio.|  
|[Clon](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-getcount.md)|Obtiene el número de puntos de interrupción de error de un enumerador.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz contiene una lista de [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) interfaces, cada uno de los cuales describe un punto de interrupción que no se pudo enlazar y por qué no se pudo enlazar. Visual Studio usa el `IEnumDebugErrorBreakpoint2` interfaz para actualizar los puntos de interrupción se muestra en el IDE.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)