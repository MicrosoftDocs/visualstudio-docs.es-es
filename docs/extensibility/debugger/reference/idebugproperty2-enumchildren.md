---
title: "IDebugProperty2::EnumChildren | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::EnumChildren"
helpviewer_keywords: 
  - "IDebugProperty2::EnumChildren"
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProperty2::EnumChildren
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

recupera una lista de los elementos secundarios de la propiedad.  
  
## Sintaxis  
  
```cpp#  
HRESULT EnumChildren (   
   DEBUGPROP_INFO_FLAGS      dwFields,  
   DWORD                     dwRadix,  
   REFGUID                   guidFilter,  
   DBG_ATTRIB_FLAGS          dwAttribFilter,  
   LPCOLESTR                 pszNameFilter,  
   DWORD                     dwTimeout,  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```c#  
int EnumChildren (   
   enum_DEBUGPROP_INFO_FLAGS   dwFields,  
   uint                        dwRadix,  
   ref Guid                    guidFilter,  
   uint                        dwAttribFilter,  
   string                      pszNameFilter,  
   uint                        dwTimeout,  
   out IEnumDebugPropertyInfo2 ppEnum  
);  
```  
  
#### Parámetros  
 `dwFields`  
 \[in\]  Una combinación de marcadores de enumeración de [DEBUGPROP\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) que especifica qué campos en las estructuras enumeradas de [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) se deben completar.  
  
 `dwRadix`  
 \[in\]  Especifica la base que se utilizará para dar formato a cualquier información numérica.  
  
 `guidFilter`  
 \[in\]  GUID del filtro utilizado con parámetros de `dwAttribFilter` y de `pszNameFilter` a seleccionar los elementos secundarios de `DEBUG_PROPERTY_INFO` deben ir.  por ejemplo, filtros de `guidFilterLocals` para las variables locales.  
  
 `dwAttribFilter`  
 \[in\]  Una combinación de marcadores de enumeración de [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) que especifica qué tipo de objetos para enumerar, por ejemplo `DBG_ATTRIB_METHOD` para todos los métodos que pueden ser elementos secundarios de esta propiedad.  Se utiliza junto con los parámetros de `guidFilter` y de `pszNameFilter` .  
  
 `pszNameFilter`  
 \[in\]  El nombre del filtro utilizado con parámetros de `guidFilter` y de `dwAttribFilter` a seleccionar los elementos secundarios de `DEBUG_PROPERTY_INFO` deben ir.  Por ejemplo, si establece este parámetro en los filtros de “MyX” para todos los elementos secundarios con el nombre “MyX.”  
  
 `dwTimeout`  
 \[in\]  Especifica el tiempo máximo, en milisegundos, de esperar antes de volver de este método.  uso `INFINITE` de esperar indefinidamente.  
  
 `ppEnum`  
 \[out\]  devuelve un objeto de [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) que contiene una lista de las propiedades secundarias.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; si no devuelve un código de error.  
  
## Vea también  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [DEBUGPROP\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)