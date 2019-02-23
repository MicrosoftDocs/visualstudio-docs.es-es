---
title: Visualización de datos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 852616ac77096a5b31078d64051f67f6cbb3ecb6
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56683383"
---
# <a name="visualizing-and-viewing-data"></a>Visualización de datos
Los visualizadores de tipo y presentar los datos de forma que sea significativo rápidamente a un desarrollador visores personalizados. El evaluador de expresiones (EE) puede admiten visualizadores de tipo de terceros, así como proporcionar sus propios visores personalizados.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Determina el número de visualizadores de tipo y visores personalizados están asociados con el tipo del objeto mediante una llamada a la [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) método. Si hay visualizador al menos un tipo o el visor personalizado disponible, Visual Studio llama el [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) método para recuperar una lista de dichos visualizadores y visores (en realidad, una lista de s que implementa los visualizadores y visores) y los presenta al usuario.

## <a name="supporting-type-visualizers"></a>Compatibilidad con los visualizadores de tipo
 Hay una serie de interfaces que debe implementar el EE para admitir los visualizadores de tipo. Estas interfaces pueden dividirse en dos amplias categorías: las interfaces que se muestran los visualizadores de tipo y las interfaces que tienen acceso a los datos de propiedad.

### <a name="listing-type-visualizers"></a>Visualizadores de tipo de lista
 EE admite la enumeración de los visualizadores de tipo en su implementación de `IDebugProperty3::GetCustomViewerCount` y `IDebugProperty3::GetCustomViewerList`. Estos métodos pasan la llamada a los métodos correspondientes [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) y [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).

 El [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) se obtiene mediante una llamada a [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Este método requiere la [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) interfaz, que se obtiene de la [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) interfaz pasa a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). `IEEVisualizerServiceProvider::CreateVisualizerService` También requiere la [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) y [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) interfaces, que se pasaron a `IDebugParsedExpression::EvaluateSync`. La interfaz final necesaria para crear el `IEEVisualizerService` interfaz es la [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) interfaz, que implementa lo EE. Esta interfaz permite que se realicen cambios en la propiedad que se visualiza. Todos los datos de la propiedad se encapsula en un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) interfaz, que también se implementa mediante lo EE.

### <a name="accessing-property-data"></a>Acceso a los datos de propiedad
 Acceso a datos de la propiedad se realiza a través de la [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) interfaz. Para obtener esta interfaz, Visual Studio llama [QueryInterface](/cpp/atl/queryinterface) en el objeto de propiedad para obtener el [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) interfaz (implementado en el mismo objeto que implementa el [ IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) interfaz) y, a continuación, llama a la [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) método para obtener el `IPropertyProxyEESide` interfaz.

 Todos los datos se pasan dentro y fuera de la `IPropertyProxyEESide` interfaz se encapsula en la [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) interfaz. Esta interfaz representa una matriz de bytes y se implementa mediante Visual Studio y en lo EE. Cuando los datos de una propiedad se va a cambiar, Visual Studio crea un `IEEDataStorage` objeto que contiene los nuevos datos y las llamadas [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) con ese objeto de datos con el fin de obtener un nuevo `IEEDataStorage` objeto que, a su vez, pasa a [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) para actualizar los datos de la propiedad. `IPropertyProxyEESide::CreateReplacementObject` permite la EE crear instancias de su propia clase que implementa el `IEEDataStorage` interfaz.

## <a name="supporting-custom-viewers"></a>Compatibilidad con los visores personalizados
 La marca `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` está establecido el `dwAttrib` campo de la [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) estructura (devuelto por una llamada a [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)) para indicar que el objeto tiene un visor personalizado asociado con él. Cuando se establece esta marca, Visual Studio obtiene el [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) interfaz desde el [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) mediante la interfaz [QueryInterface](/cpp/atl/queryinterface).

 Si el usuario selecciona un visor personalizado, Visual Studio crea una instancia del visor personalizado usando el Visor `CLSID` proporcionado por el `IDebugProperty3::GetCustomViewerList` método. Visual Studio, a continuación, llama [valor de visualización](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) para mostrar el valor para el usuario.

 Normalmente, `IDebugCustomViewer::DisplayValue` presenta una vista de solo lectura de los datos. Para permitir que los cambios realizados en los datos, el EE debe implementar una interfaz personalizada que admita los datos que cambian en un objeto de propiedad. El `IDebugCustomViewer::DisplayValue` método usa esta interfaz personalizada que se pueden cambiar los datos. El método busca la interfaz personalizada el `IDebugProperty2` interfaz pasa como el `pDebugProperty` argumento.

## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Compatibilidad con los visualizadores de tipo y visores personalizados
 Puede admitir un EE visualizadores de tipo y visores personalizados en el [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) y [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) métodos. En primer lugar, el EE agrega el número de visores personalizados que suministra con el valor devuelto por la [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) método. En segundo lugar, se anexa el EE el `CLSID`s de sus propios visores personalizados para la lista devuelta por la [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) método.

## <a name="see-also"></a>Vea también
- [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)
- [Visualizador de tipo y visor personalizado](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)