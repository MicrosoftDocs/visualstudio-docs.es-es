---
title: "IPropertyProxyEESide | Microsoft Docs"
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
  - "IPropertyProxyEESide"
helpviewer_keywords: 
  - "Interfaz IPropertyProxyEESide"
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IPropertyProxyEESide
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz proporciona métodos a los datos de la vista en el objeto asociado.  Esta interfaz es parte de la compatibilidad con los visualizadores escritos.  
  
## Sintaxis  
  
```  
IPropertyProxyEESide : IUnknown  
```  
  
## Notas para los implementadores  
 Un evaluador de expresiones implementa esta interfaz para admitir los visualizadores de tipo.  
  
## Notas para los llamadores  
 llamada [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) para obtener esta interfaz.  Llame a [QueryInterface](/visual-cpp/atl/queryinterface) en una interfaz de [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) para obtener la interfaz de [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) .  
  
## métodos en el orden de Vtable  
 Los siguientes métodos se implementan mediante esta interfaz:  
  
|Método|Descripción|  
|------------|-----------------|  
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|Inicializa un proveedor del origen de datos para que se pueda obtener acceso a los datos de objeto.|  
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|Recupera información sobre el ensamblado del objeto.|  
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|obtiene los datos iniciales para el objeto.|  
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|Crea una copia de un almacén de datos existentes.|  
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|Crea una referencia a un almacén de datos existentes.|  
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|Recupera información sobre un ensamblado concreto en el contexto del ensamblado que contiene este objeto.|  
  
## Comentarios  
 Un visualizador de tipo utiliza esta interfaz para tener acceso a los valores asociados con el objeto que esta interfaz forma parte de.  Los datos a través de la interfaz de [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) , que proporciona una vista de solo lectura de los datos.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Visualizador de tipo y el visor personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)