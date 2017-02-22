---
title: "IDebugStackFrame2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame2"
helpviewer_keywords: 
  - "Interfaz IDebugStackFrame2"
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugStackFrame2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz representa un solo marco de pila en una pila de llamadas en un subproceso concreto.  
  
## Sintaxis  
  
```  
IDebugStackFrame2 : IUnknown  
```  
  
## Notas para los implementadores  
 El motor de depuración \(DE\) implementa esta interfaz para representar un marco de pila.  
  
## Notas para los llamadores  
 llamada [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) para recuperar una interfaz de [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) .  Llame a [Siguiente](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) para recuperar una estructura de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) que contiene la interfaz de `IDebugStackFrame2` .  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugStackFrame2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Obtiene el contexto de código para este marco de pila.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Obtiene el contexto del documento para este marco de pila.|  
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Obtiene el nombre del marco de pila.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Obtiene una descripción del marco de pila.|  
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Obtiene una representación equipo\-dependiente de intervalo de direcciones físicas asociado a un marco de pila.|  
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Obtiene un contexto de evaluación para realizar la evaluación de expresiones en el contexto actual de un marco de pila y un subproceso.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Obtiene el idioma asociado a un marco de pila.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Obtiene una descripción de las propiedades asociadas con un marco de pila.|  
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|Crea un enumerador para las propiedades de marco de pila.|  
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|obtiene el subproceso asociado con un marco de pila.|  
  
## Comentarios  
 Se obtiene esta interfaz cuando el programa que se depura se ha detenido en un punto de interrupción \(provocado por un punto de interrupción del conjunto de usuarios o una excepción\).  De esta interfaz, un contexto de expresiones se pueden recopilar para evaluar expresiones, una lista de registros puede ser devuelta, o la pila de llamadas puede obtenerse y ser examinada.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)