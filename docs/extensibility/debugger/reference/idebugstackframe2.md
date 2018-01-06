---
title: IDebugStackFrame2 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugStackFrame2
helpviewer_keywords: IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 457cfc4997ca02ca76b296e3b56fded244629e52
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
Esta interfaz representa un marco de pila solo en una pila de llamadas en un subproceso determinado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugStackFrame2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (Alemania) implementa esta interfaz para representar un marco de pila.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Llame a [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) para recuperar un [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) interfaz. Llame a [siguiente](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) para recuperar un [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) estructura que contiene el `IDebugStackFrame2` interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugStackFrame2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Obtiene el contexto del código para este marco de pila.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Obtiene el contexto del documento de este marco de pila.|  
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Obtiene el nombre del marco de pila.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Obtiene una descripción del marco de pila.|  
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Obtiene una representación dependientes del equipo del intervalo de direcciones físicas asociado a un marco de pila.|  
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Obtiene un contexto de evaluación para realizar la evaluación de expresiones en el contexto actual de un marco de pila y subproceso.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Obtiene el idioma asociado a un marco de pila.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Obtiene una descripción de las propiedades asociadas a un marco de pila.|  
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|Crea un enumerador para la pila de propiedades del marco.|  
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Obtiene el subproceso asociado a un marco de pila.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz se obtiene cuando se ha detenido el programa que se está depurando en un punto de interrupción (ya sea causada por un punto de interrupción definidos por el usuario o una excepción). De esta interfaz, se puede obtener el contexto de una expresión para evaluar expresiones, se puede devolver una lista de registros o pueden obtener y examinar la pila de llamadas.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)