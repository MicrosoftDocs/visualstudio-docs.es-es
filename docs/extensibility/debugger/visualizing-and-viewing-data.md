---
title: "Visualizar y visualización de datos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 3f2317abd4bfaf6ebf8151812cf15541a1c94ecf
ms.lasthandoff: 04/05/2017

---
# <a name="visualizing-and-viewing-data"></a>Visualizar y visualización de datos
Los visualizadores de tipo y presentar los datos de forma que sea significativo rápidamente a un desarrollador visores personalizados. El evaluador de expresiones (EE) puede admiten visualizadores de tipo de terceros, así como proporcionar sus propios visores personalizados.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]determina cuántas visualizadores de tipo y los visores personalizados están asociados con el tipo del objeto mediante una llamada a la [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) método. Si hay visualizador de al menos un tipo o el visor personalizado disponible, Visual Studio llama a la [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) método para recuperar una lista de los visualizadores y visores (en realidad, una lista de `CLSID`s que implementan los visores y visualizadores) y se presenta al usuario.  
  
## <a name="supporting-type-visualizers"></a>Compatibilidad con los visualizadores de tipo  
 Hay una serie de interfaces que debe implementar el EE para admitir los visualizadores de tipo. Estas interfaces pueden dividirse en dos amplias categorías: aquellos que se enumeran los visualizadores de tipo y los que tienen acceso a los datos de propiedad.  
  
### <a name="listing-type-visualizers"></a>Visualizadores de tipo de lista  
 El EE admite enumerar los visualizadores de tipo en su implementación de `IDebugProperty3::GetCustomViewerCount` y `IDebugProperty3::GetCustomViewerList`. Estos métodos pasan la llamada a los métodos correspondientes [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) y [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).  
  
 El [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) se obtiene mediante una llamada a [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Este método requiere la [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) interfaz, que se obtiene de la [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) interfaz se pasa a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). `IEEVisualizerServiceProvider::CreateVisualizerService`También requiere la [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) y [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) interfaces que se pasaron a `IDebugParsedExpression::EvaluateSync`. La interfaz final necesaria para crear el `IEEVisualizerService` interfaz es la [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) interfaz, que implementa lo EE. Esta interfaz permite que los cambios que se realizan en la propiedad que está visualizándose. Todos los datos de propiedad se encapsula en un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) interfaz, que también se implementa mediante lo EE.  
  
### <a name="accessing-property-data"></a>Acceso a los datos de propiedad  
 Acceso a datos de la propiedad se realiza a través de la [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) interfaz. Para obtener esta interfaz, llama a Visual Studio [QueryInterface](/cpp/atl/queryinterface) del objeto de propiedad que se va a obtener el [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) interfaz (implementado en el mismo objeto que implementa el [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) interfaz) y, a continuación, llama a la [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) método para obtener el `IPropertyProxyEESide` interfaz.  
  
 Todos los datos pasan dentro y fuera de la `IPropertyProxyEESide` interfaz se encapsula en la [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) interfaz. Esta interfaz representa una matriz de bytes y se implementa mediante Visual Studio y de lo EE. Cuando los datos de una propiedad se va a cambiar, Visual Studio crea un `IEEDataStorage` objeto que contiene los nuevos datos y llamadas [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) con objeto de datos con el fin de obtener un nuevo `IEEDataStorage` objeto que, a su vez, se pasa a [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) para actualizar los datos de la propiedad. `IPropertyProxyEESide::CreateReplacementObject`permite la EE crear instancias de su propia clase que implementa el `IEEDataStorage` interfaz.  
  
## <a name="supporting-custom-viewers"></a>Visores personalizados auxiliares  
 La marca `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` está establecido el `dwAttrib` campo de la [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) estructura (devuelto por una llamada a [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)) para indicar que el objeto tiene un visor personalizado asociado con él. Cuando se establece esta marca, Visual Studio obtiene la [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) interfaz desde el [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) mediante la interfaz [QueryInterface](/cpp/atl/queryinterface).  
  
 Si el usuario selecciona un visor personalizado, Visual Studio crea el visor personalizado usando el Visor `CLSID` proporcionado por el `IDebugProperty3::GetCustomViewerList` método. Visual Studio, a continuación, llama a [valor de visualización](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) para mostrar el valor para el usuario.  
  
 Normalmente, `IDebugCustomViewer::DisplayValue` presenta una vista de solo lectura de los datos. Para permitir cambios en los datos, el EE debe implementar una interfaz personalizada que admita los datos que cambian en un objeto de propiedad. El `IDebugCustomViewer::DisplayValue` método usa esta interfaz personalizada que admite el cambio de los datos. El método busca la interfaz personalizada el `IDebugProperty2` interfaz se pasa como el `pDebugProperty` argumento.  
  
## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Soporte escriba visualizadores y visores personalizados  
 Puede admitir un EE visualizadores de tipo y los visores personalizados en el [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) y [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) métodos. En primer lugar, el EE suma el número de visores personalizados que suministra con el valor devuelto por la [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) método. En segundo lugar, se anexa el EE el `CLSID`s de sus propios visores personalizados para la lista devuelta por la [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) método.  
  
## <a name="see-also"></a>Vea también  
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)   
 [Visualizador de tipo y visor personalizado](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
