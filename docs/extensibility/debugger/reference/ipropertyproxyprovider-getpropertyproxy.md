---
title: "IPropertyProxyProvider::GetPropertyProxy | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IPropertyProxyProvider::GetPropertyProxy"
helpviewer_keywords: 
  - "IPropertyProxyProvider::GetPropertyProxy"
ms.assetid: 3ebb7515-5bfe-48f4-9b8d-721b8f664eb6
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IPropertyProxyProvider::GetPropertyProxy
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera la interfaz de proxy de propiedad para el identificador especificado de proxy  
  
## Sintaxis  
  
```cpp#  
HRESULT GetPropertyProxy(  
   DWORD                  dwID,  
   IPropertyProxyEESide** proxy  
);  
```  
  
```c#  
int GetPropertyProxy(  
   uint                     dwID,  
   out IPropertyProxyEESide proxy  
);  
```  
  
#### Parámetros  
 `dwID`  
 \[in\]  Identificador del proxy deseado de la propiedad.  
  
 `proxy`  
 \[out\]  devuelve un objeto de [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) .  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Para admitir los visualizadores de tipo externo, este método transmite normalmente la llamada al método de [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md) .  Vea [Visualizar y visualización de datos](../../../extensibility/debugger/visualizing-and-viewing-data.md) para obtener detalles sobre cómo se recopilan IEEVisualizerService.  
  
## Vea también  
 [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [Visualizar y visualización de datos](../../../extensibility/debugger/visualizing-and-viewing-data.md)