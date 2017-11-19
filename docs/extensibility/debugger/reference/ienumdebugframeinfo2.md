---
title: IEnumDebugFrameInfo2 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugFrameInfo2
helpviewer_keywords: IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c9c0cd58c069989b9516d707ba4c9a35faf53013
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
Esta interfaz enumera [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) estructuras.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IEnumDebugFrameInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (Alemania) implementa esta interfaz para proporcionar una lista de estructuras que describe la pila de llamadas actual.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Llamadas visuales Studio [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) para obtener esta interfaz siempre que sea un punto de interrupción, excepción o detención se produce en un programa que se está depurando.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IEnumDebugFrameInfo2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Recupera un número especificado de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) estructuras en una secuencia de enumeración.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Omite un número especificado de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) estructuras en una secuencia de enumeración.|  
|[Restablecer](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Restablece una secuencia de enumeración al principio.|  
|[Clon](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Obtiene el número de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) estructuras en un enumerador.|  
  
## <a name="remarks"></a>Comentarios  
 Visual Studio obtiene esta interfaz como el primer paso para controlar un punto de interrupción, excepción o generado por el usuario pausa en el programa que se está depurando. La lista de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) estructuras representa la pila de llamadas actual, con la llamada de función actual al principio de la lista y la función más antigua de llamadas al final de la lista. Cada `FRAMEINFO` representa un marco de pila y un contexto en el que se pueden evaluar expresiones y examinando las variables locales.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)