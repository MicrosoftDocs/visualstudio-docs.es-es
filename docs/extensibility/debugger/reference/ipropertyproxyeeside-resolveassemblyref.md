---
title: "IPropertyProxyEESide::ResolveAssemblyRef | Microsoft Docs"
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
  - "IPropertyProxyEESide::ResolveAssemblyRef"
helpviewer_keywords: 
  - "IPropertyProxyEESide::ResolveAssemblyRef"
ms.assetid: 662ca0a6-dad0-4c00-a718-bb3bbc5bd9da
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IPropertyProxyEESide::ResolveAssemblyRef
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Determina la ubicación de la referencia administrada especificada del ensamblado.  
  
## Sintaxis  
  
```cpp#  
HRESULT ResolveAssemblyRef(  
   BSTR*                  assemName,  
   IEEDataStorage**       assemBytes,  
   IEEDataStorage**       assemPdb,  
   BSTR*                  assemLocation,  
   ASSEMBLYLOCRESOLUTION* alr  
);  
```  
  
```c#  
int ResolveAssemblyRef(  
   ref string                     assemName,  
   out IEEDataStorage             assemBytes,  
   out IEEDataStorage             assemPdb,  
   out string                     assemLocation,  
   out enum_ASSEMBLYLOCRESOLUTION alr  
);  
```  
  
#### Parámetros  
 `assemName`  
 \[in\]  Nombre del ensamblado a resolver.  
  
 `assemBytes`  
 \[out\]  Devuelve un objeto de [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) que contiene los bytes del ensamblado asociado a la referencia.  
  
 `assemPdb`  
 \[out\]  Devuelve un objeto de `IEEDataStorage` que contiene los datos del almacén de símbolos asociado a esta referencia.  
  
 `assemLocation`  
 \[out\]  Devuelve la ubicación de la ruta de acceso de esta referencia.  
  
 `alr`  
 \[out\]  Devuelve un valor de enumeración de [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) que indica la ubicación del ensamblado de esta referencia.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Este método no se implementa normalmente por un evaluador de expresiones personalizado.  
  
## Vea también  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)