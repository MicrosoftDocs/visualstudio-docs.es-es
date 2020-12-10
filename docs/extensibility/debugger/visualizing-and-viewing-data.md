---
title: Visualizar y ver datos | Microsoft Docs
description: Obtenga información sobre cómo los visualizadores de tipos y los visores personalizados presentan datos a un desarrollador. El evaluador de expresiones admite visualizadores de tipo de terceros.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 856788546e10e69a8bb7e2787558505937f9effd
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995465"
---
# <a name="visualizing-and-viewing-data"></a>Visualizar y ver datos
Los visualizadores de tipos y los visores personalizados presentan datos de una manera que es rápidamente significativa para un desarrollador. El evaluador de expresiones (EE) puede admitir visualizadores de tipo de terceros, así como proporcionar sus propios visores personalizados.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] determina cuántos visualizadores de tipos y visores personalizados están asociados al tipo del objeto llamando al método [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) . Si hay al menos un visualizador de tipos o un visor personalizado disponible, Visual Studio llama al método [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) para recuperar una lista de los visualizadores y visores (en realidad, una lista de s que implementa los visualizadores y visores) y los presenta al usuario.

## <a name="supporting-type-visualizers"></a>Visualizadores de tipos compatibles
 Hay una serie de interfaces que el EE debe implementar para admitir los visualizadores de tipos. Estas interfaces se pueden dividir en dos amplias categorías: interfaces que enumeran los visualizadores de tipo e interfaces que tienen acceso a los datos de la propiedad.

### <a name="listing-type-visualizers"></a>Enumerar visualizadores de tipos
 EE permite enumerar los visualizadores de tipos en su implementación de `IDebugProperty3::GetCustomViewerCount` y `IDebugProperty3::GetCustomViewerList` . Estos métodos pasan la llamada a los métodos correspondientes [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) y [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).

 El [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) se obtiene llamando a [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Este método requiere la interfaz [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) , que se obtiene de la interfaz [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) pasada a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). `IEEVisualizerServiceProvider::CreateVisualizerService` también requiere las interfaces [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) y [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) , que se pasaron a `IDebugParsedExpression::EvaluateSync` . La interfaz final necesaria para crear la `IEEVisualizerService` interfaz es la interfaz [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) , que el EE implementa. Esta interfaz permite realizar cambios en la propiedad que se visualiza. Todos los datos de propiedad se encapsulan en una interfaz [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) , que también se implementa mediante el.

### <a name="accessing-property-data"></a>Obtener acceso a los datos de propiedad
 El acceso a los datos de la propiedad se realiza a través de la interfaz [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) . Para obtener esta interfaz, Visual Studio llama a [QueryInterface](/cpp/atl/queryinterface) en el objeto de propiedad para obtener la interfaz [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) (implementada en el mismo objeto que implementa la interfaz [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) ) y, a continuación, llama al método [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) para obtener la `IPropertyProxyEESide` interfaz.

 Todos los datos que se pasan dentro y fuera de la `IPropertyProxyEESide` interfaz se encapsulan en la interfaz [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) . Esta interfaz representa una matriz de bytes y se implementa tanto en Visual Studio como en EE. Cuando los datos de una propiedad se van a cambiar, Visual Studio crea un `IEEDataStorage` objeto que contiene los datos nuevos y llama a [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) con ese objeto de datos para obtener un nuevo `IEEDataStorage` objeto que, a su vez, se pasa a [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) para actualizar los datos de la propiedad. `IPropertyProxyEESide::CreateReplacementObject` permite que el EE cree una instancia de su propia clase que implementa la `IEEDataStorage` interfaz.

## <a name="supporting-custom-viewers"></a>Admitir visores personalizados
 La marca `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` se establece en el `dwAttrib` campo de la estructura de [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) (devuelta por una llamada a [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)) para indicar que el objeto tiene un visor personalizado asociado a él. Cuando se establece esta marca, Visual Studio obtiene la interfaz [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) de la interfaz [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) mediante [QueryInterface](/cpp/atl/queryinterface).

 Si el usuario selecciona un visor personalizado, Visual Studio crea una instancia del visor personalizado mediante el uso del visor `CLSID` proporcionado por el `IDebugProperty3::GetCustomViewerList` método. A continuación, Visual Studio llama a [DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) para mostrar el valor al usuario.

 Normalmente, `IDebugCustomViewer::DisplayValue` presenta una vista de solo lectura de los datos. Para permitir cambios en los datos, el EE debe implementar una interfaz personalizada que admita el cambio de datos en un objeto de propiedad. El `IDebugCustomViewer::DisplayValue` método utiliza esta interfaz personalizada para admitir el cambio de los datos. El método busca la interfaz personalizada en la `IDebugProperty2` interfaz que se pasa como `pDebugProperty` argumento.

## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Compatibilidad con visualizadores de tipos y visores personalizados
 Un EE puede admitir tanto visualizadores de tipos como visores personalizados en los métodos [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) y [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) . En primer lugar, el EE agrega el número de visores personalizados que se suministran al valor devuelto por el método [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) . En segundo lugar, el EE anexa el `CLSID` s de sus propios visores personalizados a la lista devuelta por el método [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) .

## <a name="see-also"></a>Consulte también
- [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)
- [Visualizador de tipos y visor personalizado](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
