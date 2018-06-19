---
title: IDebugStackFrame2::EnumProperties | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame2::EnumProperties
helpviewer_keywords:
- IDebugStackFrame2::EnumProperties
ms.assetid: 334bb95e-c7e0-4008-9f06-8c3999e47ee8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c0f32eac31b9b42a263ee57925f1fa8a785a1131
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120798"
---
# <a name="idebugstackframe2enumproperties"></a>IDebugStackFrame2::EnumProperties
Crea un enumerador para las propiedades asociadas con el marco de pila, por ejemplo, las variables locales.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT EnumProperties (   
   DEBUGPROP_INFO_FLAGS      dwFieldSpec,  
   UINT                      nRadix,  
   REFIID                    refiid,  
   DWORD                     dwTimeout,  
   ULONG*                    pcelt,  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumProperties (   
   enum_DEBUGPROP_INFO_FLAGS   dwFieldSpec,  
   uint                        nRadix,  
   ref Guid                    refiid,  
   uint                        dwTimeout,  
   out uint                    pcelt,  
   out IEnumDebugPropertyInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwFieldSpec`  
 [in] Una combinación de indicadores de la [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) enumeración que especifica los campos en el enumerado [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) estructuras son que deben rellenarse.  
  
 `nRadix`  
 [in] La base que se usará para dar formato a cualquier información numérica.  
  
 `refiid`  
 [in] Un GUID de un filtro usado para seleccionar qué [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) estructuras son deben mostrarse, como `guidFilterLocals`.  
  
 `dwTimeout`  
 [in] Tiempo máximo, en milisegundos, que se esperará antes de volver de este método. Use `INFINITE` para esperar indefinidamente.  
  
 `pcelt`  
 [out] Devuelve el número de propiedades enumeradas. Esto equivale a llamar a la [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md) método.  
  
 `ppEnum`  
 [out] Devuelve un [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) objeto que contiene una lista de las propiedades deseadas.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Dado que este método permite seleccionadas todas las propiedades que se recuperan mediante una llamada única, es más rápido que secuencialmente al llamar a la [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) y [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) métodos.  
  
## <a name="see-also"></a>Vea también  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)   
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)