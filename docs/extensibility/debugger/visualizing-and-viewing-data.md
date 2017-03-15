---
title: "Visualizar y visualizaci&#243;n de datos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depurar [SDK de depuración], ver datos"
  - "depurar [SDK de depuración], la visualización de los datos"
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Visualizar y visualizaci&#243;n de datos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Escriba los datos actuales de los visualizadores y los visores personalizados de manera que sea rápidamente significativa a un desarrollador.  El evaluador de \(EE\) expresiones puede admitir los visualizadores de terceros de tipo así como proporcionar sus propios visores personalizados.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] determina cuántos escriben los visualizadores y los visores personalizados de está asociado al tipo de objeto llamando al método de [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) .  Si hay al menos un visualizador o visor tipo personalizado de disponible, Visual Studio llama al método de [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) para recuperar una lista de los visualizadores y visores \(en realidad, una lista de s de `CLSID`que implementa los visualizadores y visores\) y los muestra al usuario.  
  
## admitir los visualizadores escritos  
 Hay varias interfaces que aa debe implementar para admitir los visualizadores de tipo.  Estas interfaces se pueden dividir en dos categorías: los que enumeran los visualizadores de tipos y los que tienen acceso a los datos de la propiedad.  
  
### enumerar los visualizadores escritos  
 Aa admite enumerar los visualizadores de tipo en su implementación de `IDebugProperty3::GetCustomViewerCount` y de `IDebugProperty3::GetCustomViewerList`.  estos métodos pasan la llamada a los métodos correspondientes [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) y [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).  
  
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) se obtiene llamando a [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md).  este método requiere la interfaz de [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) , que se obtiene de la interfaz de [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) pasada a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md).  `IEEVisualizerServiceProvider::CreateVisualizerService` también requiere que las interfaces de [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) y de [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) que se pasó a `IDebugParsedExpression::EvaluateSync`.  La interfaz final necesaria para crear la interfaz de `IEEVisualizerService` es la interfaz de [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) , que aa implementa.  Esta interfaz permite que los cambios se realizaron en la propiedad que se visualizada.  Todos los datos de propiedad se encapsula en una interfaz de [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) , que también se implementa por aa.  
  
### datos de acceso de la propiedad  
 El acceso de la propiedad se realiza a través de la interfaz de [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) .  Para obtener esta interfaz, las llamadas [QueryInterface](/visual-cpp/atl/queryinterface) de Visual Studio en el objeto de la propiedad para obtener la interfaz de [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) \(implementada en el mismo objeto que implementa la interfaz de [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) \) y llamar al método de [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) para obtener la interfaz de `IPropertyProxyEESide` .  
  
 Todos los datos pasado en y de la interfaz de `IPropertyProxyEESide` se encapsula en la interfaz de [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) .  Esta interfaz representa una matriz de bytes que se implementa mediante Visual Studio y aa.  Cuando los datos de una propiedad debe cambiar, Visual Studio crea un objeto de `IEEDataStorage` que contiene los nuevos datos y llama [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) con ese objeto de datos para obtener un nuevo objeto de `IEEDataStorage` que, a su vez, se pasa a [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) para actualizar los datos de propiedad.  `IPropertyProxyEESide::CreateReplacementObject` permite que aa cree instancias su propia clase que implemente la interfaz de `IEEDataStorage` .  
  
## admitir los visores personalizados  
 El marcador `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` se establece en el campo de `dwAttrib` de la estructura de [DEBUG\_PROPERTY\_INFO](../../extensibility/debugger/reference/debug-property-info.md) \(devuelta por una llamada a [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)\) para indicar que el objeto tiene un visor personalizado asociado.  Cuando se establece este marcador, Visual Studio obtiene la interfaz de [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) de la interfaz de [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) mediante [QueryInterface](/visual-cpp/atl/queryinterface).  
  
 Si el usuario selecciona un visor personalizado, Visual Studio crea instancias el visor personalizado mediante `CLSID` de visor proporcionado por el método de `IDebugProperty3::GetCustomViewerList` .  Visual Studio llama [Valor de visualización](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) para mostrar el valor al usuario.  
  
 Normalmente, `IDebugCustomViewer::DisplayValue` muestra una vista de solo lectura de los datos.  Para permitir cambios en los datos, aa debe implementar una interfaz personalizada que admita cambiar datos en un objeto de la propiedad.  El método de `IDebugCustomViewer::DisplayValue` utiliza esta interfaz personalizada para poder modificar los datos.  El método busca la interfaz personalizada en la interfaz de `IDebugProperty2` pasado como argumento de `pDebugProperty` .  
  
## Admitir el tipo los visualizadores de Caso y los visores personalizados  
 Aa puede admitir ambos visualizadores de tipo y visores personalizados en los métodos de [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) y de [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) .  Primero, aa agrega el número de visores personalizados que está proporcionando el valor devuelto por el método de [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) .  En segundo lugar, aa anexa s para `CLSID`de sus propios visores personalizados a la lista devuelta por el método de [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) .  
  
## Vea también  
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)   
 [Visualizador de tipo y el visor personalizado](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)