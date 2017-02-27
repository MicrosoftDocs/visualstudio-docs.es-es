---
title: "IDebugStackFrame2::EnumProperties | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame2::EnumProperties"
helpviewer_keywords: 
  - "IDebugStackFrame2::EnumProperties"
ms.assetid: 334bb95e-c7e0-4008-9f06-8c3999e47ee8
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugStackFrame2::EnumProperties
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crea un enumerador para las propiedades asociadas con el marco de pila, como las variables locales.  
  
## Sintaxis  
  
```cpp#  
HRESULT EnumProperties (   
   DEBUGPROP_INFO_FLAGS      dwFieldSpec,  
   UINT                      nRadix,  
   REFIID                    refiid,  
   DWORD                     dwTimeout,  
   ULONG*                    pcelt,  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```c#  
int EnumProperties (   
   enum_DEBUGPROP_INFO_FLAGS   dwFieldSpec,  
   uint                        nRadix,  
   ref Guid                    refiid,  
   uint                        dwTimeout,  
   out uint                    pcelt,  
   out IEnumDebugPropertyInfo2 ppEnum  
);  
```  
  
#### Parámetros  
 `dwFieldSpec`  
 \[in\]  Una combinación de marcadores de enumeración de [DEBUGPROP\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) que especifica qué campos en las estructuras enumeradas de [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) se deben completar.  
  
 `nRadix`  
 \[in\]  La base que se utilizará para dar formato a cualquier información numérica.  
  
 `refiid`  
 \[in\]  GUID de un filtro se usa para seleccionar las estructuras de [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) deben ser mostradas, por ejemplo `guidFilterLocals`.  
  
 `dwTimeout`  
 \[in\]  hora máxima, en milisegundos, de esperar antes de volver de este método.  uso `INFINITE` de esperar indefinidamente.  
  
 `pcelt`  
 \[out\]  devuelve el número de propiedades enumeradas.  Es igual que llamar al método de [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md) .  
  
 `ppEnum`  
 \[out\]  devuelve un objeto de [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) que contiene una lista de las propiedades deseadas.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Dado que este método permite que todas las propiedades seleccionadas son recuperadas con una única llamada, es más rápido que secuencialmente llamando a los métodos de [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) y de [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) .  
  
## Vea también  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [DEBUGPROP\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)   
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)