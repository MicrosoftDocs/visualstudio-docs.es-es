---
title: IDebugCustomViewer | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCustomViewer
helpviewer_keywords: IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9bbe546ffb3c6e61b251e8afbfc7fa9018ffa1b0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
Esta interfaz permite que un evaluador de expresiones (EE) para mostrar el valor de una propiedad en el mismo formato que es necesario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugCustomViewer : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un EE implementa esta interfaz para mostrar el valor de una propiedad en un formato personalizado.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Una llamada a COM `CoCreateInstance` función crea una instancia de esta interfaz. El `CLSID` pasado a `CoCreateInstance` se obtiene del registro. Una llamada a [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) Obtiene la ubicación en el registro. Vea la sección Comentarios para obtener más información, así como en el ejemplo.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Esta interfaz implementa el método siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[Valor de visualización](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|No lo que es necesario para mostrar un valor determinado.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz se utiliza cuando no se puede mostrar el valor de una propiedad por medios normales, por ejemplo, con una tabla de datos u otro tipo de propiedad compleja. Un visor personalizado, como representado por la `IDebugCustomViewer` de la interfaz, es diferente de un visualizador de tipo, que es un programa externo para mostrar datos de un tipo específico, independientemente de lo EE. El EE implementa un visor personalizado que es específico de ese EE. Un usuario selecciona el tipo del visualizador para usar, ya sea un visualizador de tipo o un visor personalizado. Vea [Visualizing y ver datos](../../../extensibility/debugger/visualizing-and-viewing-data.md) para obtener más información acerca de este proceso.  
  
 Un visor personalizado se registra en la misma manera que una EE y, por lo tanto, requiere un GUID de lenguaje y un GUID de proveedor. La métrica exacto (o nombre de la entrada del registro) se conoce solo en lo EE. Esta métrica se devuelve en el [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) estructura, que a su vez, se devuelve mediante una llamada a [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md). El valor almacenado en la métrica es la `CLSID` que se pasa a COM `CoCreateInstance` función (vea el ejemplo).  
  
 El [aplicaciones auxiliares de SDK para depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) función, `SetEEMetric`, puede utilizarse para registrar un visor personalizado. Vea la sección de "Evaluadores de expresión" del registro de `Debugging SDK Helpers` para claves del Registro específicas que necesita un visor personalizado. Observe que un visor personalizado tiene solo una métrica (que se define mediante el implementador del EE), mientras que un evaluador de expresiones requiere varias métricas predefinidas.  
  
 Normalmente, un visor personalizado proporciona una vista de solo lectura de los datos, ya que la [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaz proporcionado a [valor de visualización](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) no tiene métodos para cambiar el valor de la propiedad excepto como una cadena. Con el fin de admitir cambiar arbitrarios bloques de datos, lo EE implementa una interfaz personalizada en el mismo objeto que implementa el `IDebugProperty3` interfaz. Esta interfaz personalizada, a continuación, proporciona los métodos necesarios para cambiar un bloque de datos arbitrario.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo muestra cómo obtener el primer visor personalizado de una propiedad si esa propiedad tiene los visores personalizados.  
  
```cpp  
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
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [Aplicaciones auxiliares SDK para la depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)