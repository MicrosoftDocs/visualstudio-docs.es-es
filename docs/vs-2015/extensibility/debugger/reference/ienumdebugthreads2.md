---
title: IEnumDebugThreads2 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9b60d62846ce777897784e005457fe6cf2ca272a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51754518"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Este interfac enumera los subprocesos que se ejecutan en la sesión de depuración actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IEnumDebugThreads2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (DE) implementa esta interfaz para representar una lista de subprocesos de un programa.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Llame a [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) para obtener esta interfaz que representa una lista de todos los subprocesos de todos los programas que se ejecutan en un proceso. Llame a [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) para obtener esta interfaz que representa una lista de subprocesos que se ejecutan en un programa.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IEnumDebugThreads2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Recupera un número especificado de subprocesos en la secuencia de enumeración.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Omite un número especificado de subprocesos en una secuencia de enumeración.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Restablece una secuencia de enumeración al principio.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el actual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Obtiene el número de subprocesos de un enumerador.|  
  
## <a name="remarks"></a>Comentarios  
 Visual Studio normalmente obtiene esta interfaz para actualizar el **subprocesos** ventana, así como para obtener el primer subproceso de la lista, para poder llamar a [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [continuar](../../../extensibility/debugger/reference/idebugprocess3-continue.md), y [Paso](../../../extensibility/debugger/reference/idebugprocess3-step.md).  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces del núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)   
 [Paso](../../../extensibility/debugger/reference/idebugprocess3-step.md)   
 [Continuar](../../../extensibility/debugger/reference/idebugprocess3-continue.md)   
 [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)

