---
title: "IDebugCustomViewer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomViewer"
helpviewer_keywords: 
  - "Interfaz IDebugCustomViewer"
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugCustomViewer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz permite a un evaluador de \(EE\) expresiones para mostrar un valor de propiedad en cualquier formato es necesario.  
  
## Sintaxis  
  
```  
IDebugCustomViewer : IUknown  
```  
  
## Notas para los implementadores  
 Aa implementa esta interfaz para mostrar un valor de propiedad en un formato personalizado.  
  
## Notas para los llamadores  
 Una llamada a la función de `CoCreateInstance` de COM crea instancias de esta interfaz.  `CLSID` pasado a `CoCreateInstance` se obtiene del registro.  Una llamada a [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) obtiene la ubicación del registro.  Vea las notas de detalles junto con el ejemplo.  
  
## métodos en el orden de Vtable  
 esta interfaz implementa el método siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[Valor de visualización](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Haga lo que sea necesario mostrar un valor determinado.|  
  
## Comentarios  
 Se utiliza esta interfaz cuando un valor de propiedad no se puede mostrar por normal medio\-para el ejemplo, con una tabla de datos u otro tipo de propiedad complejo.  Un visor personalizado, como se representa por la interfaz de `IDebugCustomViewer` , es diferente de un visualizador de tipo, que es un programa externo para mostrar datos de un tipo específico independientemente aa.  Aa implementa un visor personalizado que sea específico de esa aa.  Un usuario selecciona qué tipo de visualizador a utilizar, es un visualizador de tipo o un visor personalizado.  Vea [Visualizar y visualización de datos](../../../extensibility/debugger/visualizing-and-viewing-data.md) para obtener más información sobre este proceso.  
  
 Un visor personalizado se registra igual que aa y, por consiguiente, requiere un lenguaje GUID y un proveedor GUID.  El nombre métrica \(o de entrada del Registro\) exacto sólo se conoce a aa.  Esta métrica se devuelve en la estructura de [DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) , que a su vez es devuelta por una llamada a [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md).  El valor almacenado en la métrica es `CLSID` que se pasa a la función de `CoCreateInstance` COM \(vea el ejemplo\).  
  
 la función de [Aplicaciones auxiliares SDK para la depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) , `SetEEMetric`, se puede utilizar para registrar un visor personalizado.  Vea la sección “registro de Evaluators de expresiones” de `Debugging SDK Helpers` para claves del Registro concretas que un visor personalizado debe.  Observe que un visor personalizado sólo necesita una métrica \(definido por el implementador de aa\) mientras un evaluador de expresiones requiere diversas métricas predefinidas.  
  
 Normalmente, un visor personalizado proporciona una vista de solo lectura de los datos, ya que la interfaz de [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) proporcionada a [Valor de visualización](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) no tiene métodos para cambiar el valor de propiedad excepto como cadena.  Para poder modificar bloques arbitrarios de datos, aa implementa una interfaz personalizada en el mismo objeto que implementa la interfaz de `IDebugProperty3` .  Esta interfaz personalizada a proporcionaría los métodos necesarios para cambiar un bloque arbitrario de datos.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Ejemplo  
 este ejemplo muestra cómo obtener el primer visor personalizado de una propiedad si esa propiedad tiene algunos visores personalizados.  
  
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
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [Aplicaciones auxiliares SDK para la depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)