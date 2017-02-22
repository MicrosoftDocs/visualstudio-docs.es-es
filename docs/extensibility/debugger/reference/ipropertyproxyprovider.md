---
title: "IPropertyProxyProvider | Microsoft Docs"
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
  - "IPropertyProxyProvider"
helpviewer_keywords: 
  - "Interfaz IPropertyProxyProvider"
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IPropertyProxyProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Fuentes de esta interfaz una interfaz de proxy para ver y cambiar los datos de un objeto.  
  
## Sintaxis  
  
```  
IPropertyProxyProvider : IUnknown  
```  
  
## Notas para los implementadores  
 El evaluador de \(EE\) expresiones implementa esta interfaz en el mismo objeto que implementa la interfaz de [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) como parte de la compatibilidad de aa de visualizadores escritos.  
  
## Notas para los llamadores  
 Llame a [QueryInterface](/visual-cpp/atl/queryinterface) en una interfaz de `IDebugProperty3` para obtener esta interfaz.  
  
## métodos en el orden de Vtable  
 la interfaz de `IPropertyProxyProvider` implementa el método siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Recupera una interfaz de proxy de propiedad para ver datos de un objeto.|  
  
## Comentarios  
 Aunque aa implementa esta interfaz, la implementación de [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) controla normalmente por [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md).  Vea [Visualizar y visualización de datos](../../../extensibility/debugger/visualizing-and-viewing-data.md) para obtener detalles sobre la obtención de la interfaz de IEEVisualizerService.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [Visualizador de tipo y el visor personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [Visualizar y visualización de datos](../../../extensibility/debugger/visualizing-and-viewing-data.md)