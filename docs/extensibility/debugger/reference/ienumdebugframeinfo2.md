---
title: IEnumDebugFrameInfo2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aa2db1f249492702971eb311fe38f76eec3a5b3b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53857205"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
Esta interfaz enumera [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) estructuras.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IEnumDebugFrameInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (DE) implementa esta interfaz para proporcionar una lista de estructuras que describe la pila de llamadas actual.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Llamadas visuales Studio [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) para obtener esta interfaz, cada vez que un punto de interrupción, se produce excepciones o detenerse en un programa que se está depurando.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IEnumDebugFrameInfo2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Recupera un número especificado de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) estructuras en una secuencia de enumeración.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Omite un número especificado de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) estructuras en una secuencia de enumeración.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Restablece una secuencia de enumeración al principio.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Obtiene el número de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) estructuras en un enumerador.|  
  
## <a name="remarks"></a>Comentarios  
 Visual Studio obtiene esta interfaz como el primer paso para controlar un punto de interrupción, excepción o generados por el usuario pausa en el programa que se está depurando. La lista de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) estructuras representa la pila de llamadas actual, con la llamada de función actual al principio de la lista y la función más antigua, llamar al final de la lista. Cada `FRAMEINFO` representa un marco de pila, un contexto en el que se pueden evaluar expresiones y variables locales examinado.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces del núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)