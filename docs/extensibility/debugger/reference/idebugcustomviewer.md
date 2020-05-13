---
title: IDebugCustomViewer ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c44d2289180ece35725b9258e9d20abeb3a4cac3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732422"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
Esta interfaz permite a un evaluador de expresiones (EE) mostrar el valor de una propiedad en cualquier formato necesario.

## <a name="syntax"></a>Sintaxis

```
IDebugCustomViewer : IUknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
Un EE implementa esta interfaz para mostrar el valor de una propiedad en un formato personalizado.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
Una llamada a `CoCreateInstance` la función de COM crea una instancia de esta interfaz. El `CLSID` pasado `CoCreateInstance` se obtiene del registro. Una llamada a [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) obtiene la ubicación en el registro. Consulte Comentarios para obtener más información, así como el ejemplo.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
Esta interfaz implementa el siguiente método:

|Método|Descripción|
|------------|-----------------|
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Hace lo que sea necesario para mostrar un valor determinado.|

## <a name="remarks"></a>Observaciones
Esta interfaz se utiliza cuando el valor de una propiedad no se puede mostrar por medios normales, por ejemplo, con una tabla de datos u otro tipo de propiedad compleja. Un visor personalizado, representado `IDebugCustomViewer` por la interfaz, es diferente de un visualizador de tipos, que es un programa externo para mostrar datos de un tipo específico independientemente de EE. El EE implementa un visor personalizado que es específico de ese EE. Un usuario selecciona qué tipo de visualizador usar, ya sea un visualizador de tipos o un visor personalizado. Consulte [Visualización y visualización](../../../extensibility/debugger/visualizing-and-viewing-data.md) de datos para obtener más información sobre este proceso.

Un visor personalizado se registra de la misma manera que un EE y, por lo tanto, requiere un GUID de idioma y un GUID de proveedor. La métrica exacta (o el nombre de la entrada del registro) solo la conoce el EE. Esta métrica se devuelve en la [estructura DEBUG_CUSTOM_VIEWER,](../../../extensibility/debugger/reference/debug-custom-viewer.md) que a su vez se devuelve mediante una llamada a [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md). El valor almacenado en `CLSID` la métrica es el `CoCreateInstance` que se pasa a la función de COM (consulte el ejemplo).

La función [auxiliares del SDK para depurar,](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetEEMetric`, se puede usar para registrar un visor personalizado. Consulte la sección del Registro "Evaluadores de expresiones" de `Debugging SDK Helpers` las claves de registro específicas que necesita un visor personalizado. Tenga en cuenta que un visor personalizado solo necesita una métrica (que se define mediante el implementador de EE), mientras que un evaluador de expresiones requiere varias métricas predefinidas.

Normalmente, un visor personalizado proporciona una vista de solo lectura de los datos, ya que el [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaz proporcionada a [DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) no tiene métodos para cambiar el valor de la propiedad excepto como una cadena. Con el fin de admitir el cambio de bloques arbitrarios de datos, `IDebugProperty3` el EE implementa una interfaz personalizada en el mismo objeto que implementa la interfaz. Esta interfaz personalizada proporcionaría los métodos necesarios para cambiar un bloque arbitrario de datos.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Ejemplo
En este ejemplo se muestra cómo obtener el primer visor personalizado de una propiedad si esa propiedad tiene visores personalizados.

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
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [Asistentes de SDK para la depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
