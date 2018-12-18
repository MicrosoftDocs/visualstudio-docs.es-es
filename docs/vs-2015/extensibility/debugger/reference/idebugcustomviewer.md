---
title: IDebugCustomViewer | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6b9e068591961e7eafa9d4fdc588da2694532463
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759514"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta interfaz permite que un evaluador de expresiones (EE) para mostrar el valor de una propiedad en el formato que sea necesario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugCustomViewer : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un EE implementa esta interfaz para mostrar el valor de una propiedad en un formato personalizado.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Una llamada a COM `CoCreateInstance` función crea una instancia de esta interfaz. El `CLSID` pasa a `CoCreateInstance` se obtiene del registro. Una llamada a [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) Obtiene la ubicación en el registro. Vea la sección Comentarios para obtener información detallada, así como en el ejemplo.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Esta interfaz implementa el método siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Hace que sea necesario para mostrar un valor determinado.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz se usa cuando no se puede mostrar un valor de propiedad por medios normales, por ejemplo, con una tabla de datos u otro tipo de propiedad compleja. Un visor personalizado, representada por el `IDebugCustomViewer` de la interfaz, que es diferente de un visualizador de tipo, que es un programa externo para mostrar los datos de un tipo específico, independientemente de lo EE. EE implementa un visor personalizado que es específico de ese EE. Un usuario selecciona el tipo de visualizador para usar, ya sea un visualizador de tipo o un visor personalizado. Consulte [visualización y ver datos](../../../extensibility/debugger/visualizing-and-viewing-data.md) para obtener más información sobre este proceso.  
  
 Un visor personalizado está registrado en la misma manera que una EE y, por lo tanto, requiere un GUID de lenguaje y un GUID de proveedor. La medida exacta (o el nombre de la entrada del registro) se conoce solo en lo EE. Esta métrica se devuelve en el [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) estructura, que a su vez, se devuelve mediante una llamada a [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md). El valor almacenado en la métrica es la `CLSID` que se pasa a COM `CoCreateInstance` función (consulte el ejemplo).  
  
 El [aplicaciones auxiliares de SDK para depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) función, `SetEEMetric`, se puede usar para registrar un visor personalizado. Consulte la sección del registro "Evaluadores de expresión" `Debugging SDK Helpers` para las claves del Registro específicas que se necesita un visor personalizado. Observe que un visor personalizado tiene solo una métrica (que es definida por el implementador del EE), mientras que un evaluador de expresiones requiere varias métricas predefinidas.  
  
 Normalmente, un visor personalizado proporciona una vista de solo lectura de los datos, ya que el [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaz proporcionado a [valor de visualización](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) no tiene métodos para cambiar el valor de la propiedad, excepto como una cadena. Para admitir bloques arbitrarios de datos de cambio, el EE implementa una interfaz personalizada en el mismo objeto que implementa el `IDebugProperty3` interfaz. Esta interfaz personalizada, a continuación, proporciona los métodos necesarios para cambiar un bloque de datos arbitrario.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se muestra cómo obtener el primer visor personalizado de una propiedad si esa propiedad tiene todos los visores personalizados.  
  
```cpp#  
IDebugCustomViewer *GetFirstCustomViewer(IDebugProperty2 *pProperty)  
{  
    // This string is typically defined globally.  For this example, it  
    // is defined here.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
    IDebugCustomViewer *pViewer = NULL;  
    if (pProperty != NULL) {  
        CComQIPtr<IDebugProperty3> pProperty3(pProperty);  
        if (pProperty3 != NULL) {  
            HRESULT hr;  
            ULONG viewerCount = 0;  
            hr = pProperty3->GetCustomViewerCount(&viewerCount);  
            if (viewerCount > 0) {  
                ULONG viewersFetched = 0;  
                DEBUG_CUSTOM_VIEWER viewerInfo = { 0 };  
                hr = pProperty3->GetCustomViewerList(0,  
                                                     1,  
                                                     &viewerInfo,  
                                                     &viewersFetched);  
                if (viewersFetched == 1) {  
                    CLSID clsidViewer = { 0 };  
                    CComPtr<IDebugCustomViewer> spCustomViewer;  
                    // Get the viewer's CLSID from the registry.  
                    ::GetEEMetric(viewerInfo.guidLang,  
                                  viewerInfo.guidVendor,  
                                  viewerInfo.bstrMetric,  
                                  &clsidViewer,  
                                  strRegistrationRoot);  
                    if (!IsEqualGUID(clsidViewer,GUID_NULL)) {  
                        // Instantiate the custom viewer.  
                        spCustomViewer.CoCreateInstance(clsidViewer);  
                        if (spCustomViewer != NULL) {  
                            pViewer = spCustomViewer.Detach();  
                        }  
                    }  
                }  
            }  
        }  
    }  
    return(pViewer);  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Interfaces del núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [Aplicaciones auxiliares de SDK para la depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)

