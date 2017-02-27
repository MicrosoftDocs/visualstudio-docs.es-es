---
title: "IDebugProperty2::GetPropertyInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::GetPropertyInfo"
helpviewer_keywords: 
  - "IDebugProperty2::GetPropertyInfo"
ms.assetid: 39d6e942-df72-4c84-a5d9-a386d112714c
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProperty2::GetPropertyInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtiene la estructura de [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) que describe una propiedad.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetPropertyInfo (   
   DEBUGPROP_INFO_FLAGS dwFields,  
   DWORD                nRadix,  
   DWORD                dwTimeout,  
   IDebugReference2**   rgpArgs,  
   DWORD                dwArgCount,  
   DEBUG_PROPERTY_INFO* pPropertyInfo  
);  
```  
  
```cpp#  
int GetPropertyInfo (   
   enum_DEBUGPROP_INFO_FLAGS dwFields,  
   uint                      nRadix,  
   uint                      dwTimeout,  
   IDebugReference2[]        rgpArgs,  
   uint                      dwArgCount,  
   DEBUG_PROPERTY_INFO[]     pPropertyInfo  
);  
```  
  
#### Parámetros  
 `dwFields`  
 \[in\]  Una combinación de valores de enumeración de [DEBUGPROP\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) que especifica qué campos se deben completar comentario la estructura de `pPropertyInfo` .  
  
 `nRadix`  
 \[in\]  Base que se utilizará para dar formato a cualquier información numérica.  
  
 `dwTimeout`  
 \[in\]  Especifica el tiempo máximo, en milisegundos, de esperar antes de volver de este método.  uso `INFINITE` de esperar indefinidamente.  
  
 `rgpArgs`  
 \[in, out\]  reservado para uso futuro; establezca en un valor nulo.  
  
 `dwArgCount`  
 \[in\]  reservado para uso futuro; establece en cero.  
  
 `pPropertyInfo`  
 \[out\]  Una estructura de [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) se completa con la descripción de la propiedad.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; si no devuelve un código de error.  
  
## Vea también  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [DEBUGPROP\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)