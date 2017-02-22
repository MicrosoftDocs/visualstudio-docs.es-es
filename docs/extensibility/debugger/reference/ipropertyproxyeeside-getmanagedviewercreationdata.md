---
title: "IPropertyProxyEESide::GetManagedViewerCreationData | Microsoft Docs"
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
  - "IPropertyProxyEESide::GetManagedViewerCreationData"
helpviewer_keywords: 
  - "IPropertyProxyEESide::GetManagedViewerCreationData"
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IPropertyProxyEESide::GetManagedViewerCreationData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera información sobre el visor para este tipo de propiedad para crear instancias de ese visor.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetManagedViewerCreationData(  
   BSTR*                  assemName,  
   IEEDataStorage**       assemBytes,  
   IEEDataStorage**       assemPdb,  
   BSTR*                  className,  
   ASSEMBLYLOCRESOLUTION* alr,  
   BOOL*                  replacementOk  
);  
```  
  
```c#  
int GetManagedViewerCreationData(  
   out string                     assemName,  
   out IEEDataStorage             assemBytes,  
   out IEEDataStorage             assemPdb,  
   out string                     className,  
   out enum_ASSEMBLYLOCRESOLUTION alr,  
   out int                        replacementOk  
);  
```  
  
#### Parámetros  
 `assemName`  
 \[out\]  Devuelve el nombre del ensamblado que contiene este objeto.  
  
 `assemBytes`  
 \[out\]  Devuelve un objeto de [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) que contiene los bytes del ensamblado de este objeto \(esto es un valor null si no hay bytes disponibles\).  
  
 `assemPdb`  
 \[out\]  Devuelve un objeto de `IEEDataStorage` que contiene información del almacén de símbolos para este objeto \(esto es un valor null si no hay ningún almacén de símbolos\).  
  
 `className`  
 \[out\]  devuelve el nombre de clase que contiene este objeto.  
  
 `alr`  
 \[out\]  Devuelve un valor de enumeración de [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) que indica la ubicación del ensamblado.  
  
 `replacementOk`  
 \[out\]  Devuelve cero \(`TRUE`\) si el valor de este objeto se puede cambiar; cero \(`FALSE`\) si el objeto es de solo lectura.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Este método se utiliza en los visualizadores escritos para crear instancias de un visor administrado.  
  
## Vea también  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)