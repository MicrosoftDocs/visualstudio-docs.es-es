---
title: IDebugStackFrame2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ae9cad7102fb9a82deb43b2c8820ef52e77deeed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547008"
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta interfaz representa un marco de pila único en una pila de llamadas de un subproceso determinado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugStackFrame2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor DE depuración (DE) implementa esta interfaz para representar un marco de pila.  
  
## <a name="notes-for-callers"></a>Notas para llamadores  
 Llame a [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) para recuperar una interfaz [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) . Llame a [Next](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) para recuperar una estructura [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) que contiene la `IDebugStackFrame2` interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 En la tabla siguiente se muestran los métodos de `IDebugStackFrame2` .  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Obtiene el contexto de código para este marco de pila.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Obtiene el contexto del documento para este marco de pila.|  
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Obtiene el nombre del marco de pila.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Obtiene una descripción del marco de pila.|  
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Obtiene una representación dependiente del equipo del intervalo de direcciones físicas asociadas a un marco de pila.|  
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Obtiene un contexto de evaluación para realizar la evaluación de expresiones en el contexto actual de un marco de pila y un subproceso.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Obtiene el lenguaje asociado a un marco de pila.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Obtiene una descripción de las propiedades asociadas a un marco de pila.|  
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|Crea un enumerador para las propiedades del marco de pila.|  
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Obtiene el subproceso asociado a un marco de pila.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz se obtiene solo cuando el programa que se está depurando se ha detenido en un punto de interrupción (ya sea debido a un punto de interrupción del conjunto de usuarios o una excepción). Desde esta interfaz, se puede obtener un contexto de expresión para evaluar las expresiones, se puede devolver una lista de registros o se puede obtener y examinar la pila de llamadas.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
