---
title: Visualización y visualización de datos de datos de visualización y visualización de datos de visualización Microsoft Docs
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
ms.openlocfilehash: 2b5f984e6c6a3c1c8f3835dfa93a8679ae16680a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712376"
---
# <a name="visualizing-and-viewing-data"></a>Visualización y visualización de datos
Los visualizadores de tipos y los visores personalizados presentan los datos de una manera que es rápidamente significativa para un desarrollador. El evaluador de expresiones (EE) puede admitir visualizadores de tipos de terceros, así como proporcionar sus propios visores personalizados.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]determina cuántos visualizadores de tipos y visores personalizados están asociados con el tipo del objeto mediante una llamada a la [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) método. Si hay al menos un visualizador de tipo o un visor personalizado disponible, Visual Studio llama al método [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) para recuperar una lista de esos visualizadores y visores (en realidad, una lista de s que implementa los visualizadores y visores) y los presenta al usuario.

## <a name="supporting-type-visualizers"></a>Compatibilidad con visualizadores de tipos
 Hay una serie de interfaces que EE debe implementar para admitir visualizadores de tipos. Estas interfaces se pueden dividir en dos amplias categorías: interfaces que enumeran los visualizadores de tipos y las interfaces que tienen acceso a los datos de propiedad.

### <a name="listing-type-visualizers"></a>Visualizadores de tipo de listado
 El EE admite la lista de visualizadores de tipos en su implementación de `IDebugProperty3::GetCustomViewerCount` y `IDebugProperty3::GetCustomViewerList`. Estos métodos pasan la llamada a los métodos correspondientes [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) y [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).

 El [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) se obtiene mediante una llamada a [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Este método requiere el [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) interfaz, que se obtiene de la [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) interfaz pasa a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). `IEEVisualizerServiceProvider::CreateVisualizerService`también requiere el [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) y [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) interfaces, que se pasaron a `IDebugParsedExpression::EvaluateSync`. La interfaz final `IEEVisualizerService` necesaria para crear la interfaz es la interfaz [IEEVisualizerDataProvider,](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) que implementa EE. Esta interfaz permite realizar cambios en la propiedad que se visualiza. Todos los datos de propiedad se encapsulan en un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) interfaz, que también se implementa mediante el EE.

### <a name="accessing-property-data"></a>Acceso a los datos de propiedad
 El acceso a los datos de propiedad se realiza a través de la [interfaz IPropertyProxyEESide.](../../extensibility/debugger/reference/ipropertyproxyeeside.md) Para obtener esta interfaz, Visual Studio llama a [QueryInterface](/cpp/atl/queryinterface) en el objeto de propiedad para obtener el [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) interfaz (implementada en `IPropertyProxyEESide` el mismo objeto que implementa el [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) interfaz) y, a continuación, llama a la [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) método para obtener la interfaz.

 Todos los datos pasados `IPropertyProxyEESide` dentro y fuera de la interfaz se encapsulan en la interfaz [IEEDataStorage.](../../extensibility/debugger/reference/ieedatastorage.md) Esta interfaz representa una matriz de bytes y se implementa mediante Visual Studio y EE. Cuando se van a cambiar los datos de `IEEDataStorage` una propiedad, Visual Studio crea un objeto que contiene `IEEDataStorage` los nuevos datos y llama a [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) con ese objeto de datos para obtener un nuevo objeto que, a su vez, se pasa a [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) para actualizar los datos de la propiedad. `IPropertyProxyEESide::CreateReplacementObject`permite que EE cree una instancia `IEEDataStorage` de su propia clase que implementa la interfaz.

## <a name="supporting-custom-viewers"></a>Apoyo a los espectadores personalizados
 El `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` indicador se `dwAttrib` establece en el campo de la [estructura DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) (devuelta por una llamada a [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)) para indicar que el objeto tiene un visor personalizado asociado. Cuando se establece esta marca, Visual Studio obtiene el [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) interfaz de la [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaz mediante [QueryInterface](/cpp/atl/queryinterface).

 Si el usuario selecciona un visor personalizado, Visual Studio crea `CLSID` una instancia `IDebugProperty3::GetCustomViewerList` del visor personalizado mediante el visor proporcionado por el método. Visual Studio, a continuación, llama a [DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) para mostrar el valor al usuario.

 Normalmente, `IDebugCustomViewer::DisplayValue` presenta una vista de solo lectura de los datos. Para permitir cambios en los datos, EE debe implementar una interfaz personalizada que admita el cambio de datos en un objeto de propiedad. El `IDebugCustomViewer::DisplayValue` método utiliza esta interfaz personalizada para admitir el cambio de datos. El método busca la interfaz personalizada en la `IDebugProperty2` interfaz pasada como `pDebugProperty` argumento.

## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Compatibilidad con visualizadores de tipos y visores personalizados
 Un EE puede admitir visualizadores de tipos y visores personalizados en los métodos [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) y [GetCustomViewerList.](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) En primer lugar, el EE agrega el número de visores personalizados que proporciona al valor devuelto por el [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) método. En segundo lugar, el `CLSID`EE anexa las s de sus propios visores personalizados a la lista devuelta por el [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) método.

## <a name="see-also"></a>Vea también
- [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)
- [Visualizador de tipos y visor personalizado](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
