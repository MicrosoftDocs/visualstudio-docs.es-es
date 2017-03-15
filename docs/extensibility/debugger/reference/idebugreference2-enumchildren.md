---
title: "IDebugReference2::EnumChildren | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReference2::EnumChildren"
helpviewer_keywords: 
  - "IDebugReference2::EnumChildren"
ms.assetid: 35b3c2f3-69f4-4013-b555-f847221f62e8
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugReference2::EnumChildren
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene una lista de elementos secundarios seleccionado de una referencia.  Reservado para un uso futuro.  
  
## Sintaxis  
  
```cpp#  
HRESULT EnumChildren (   
   DEBUGREF_INFO_FLAGS        dwFields,  
   DWORD                      dwRadix,  
   DBG_ATTRIB_FLAGS           dwAttribFilter,  
   LPCOLESTR                  pszNameFilter,  
   DWORD                      dwTimeout,  
   IEnumDebugReferenceInfo2** ppEnum  
);  
```  
  
```c#  
int EnumChildren (   
   enum_DEBUGREF_INFO_FLAGS     dwFields,  
   uint                         dwRadix,  
   enum_DBG_ATTRIB_FLAGS        dwAttribFilter,  
   string                       pszNameFilter,  
   uint                         dwTimeout,  
   out IEnumDebugReferenceInfo2 ppEnum  
);  
```  
  
#### Parámetros  
 `dwFields`  
 \[in\]  Una combinación de marcadores de enumeración de [DEBUGREF\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) que especifica qué campos en las estructuras enumeradas de [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) se deben completar.  
  
 `dwRadix`  
 \[in\]  La base que se utilizará para dar formato a cualquier información numérica.  
  
 `dwAttribFilter`  
 \[in\]  Una combinación de marcadores de enumeración de [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) que se utiliza como un filtro junto con el parámetro de `pszNameFilter` para seleccionar qué estructuras deben ser enumeradas.  
  
 `pszNameFilter`  
 \[in\]  Una cadena que especifica un filtro, como “MyX”, se utiliza junto con el parámetro de `dwAttribFilter` para seleccionar las estructuras que se van a mostrar.  
  
 `dwTimeout`  
 \[in\]  hora máxima, en milisegundos, de esperar antes de volver de este método.  uso `INFINITE` de esperar indefinidamente.  
  
 `ppEnum`  
 \[out\]  Devuelve un objeto de [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) que contiene una lista de las propiedades secundarias solicitadas.  
  
## Valor devuelto  
 Siempre devuelve `E_NOTIMPL`.  
  
## Vea también  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)