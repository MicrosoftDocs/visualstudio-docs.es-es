---
title: IDebugSettingsCallback2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2 interface
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2c85b54f92970dca5d712b827019300f850b03cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719941"
---
# <a name="idebugsettingscallback2"></a>IDebugSettingsCallback2
Permite que los motores de depuración lean la configuración de métricas de forma remota.

## <a name="syntax"></a>Sintaxis

```
IDebugSettingsCallback2D : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
Esta interfaz se implementa mediante la devolución de llamada de eventos del administrador de depuración de sesión y la consumen los motores de depuración. También se podría utilizar localmente en lugar de Dbgmetric[d].lib.

## <a name="methods"></a>Métodos
En la tabla siguiente `IDebugSettingsCallback2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|Enumera los evaluadores de expresiones disponibles dados los identificadores de idioma y proveedor.|
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|Recupera un objeto local del evaluador de expresiones dado la métrica.|
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|Recupera un valor que corresponde a la métrica especificada del evaluador de expresiones.|
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|Recupera el archivo de métrica del evaluador de expresiones dado el nombre o la métrica.|
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|Recupera el identificador único de una métrica de evaluador de expresiones dado su nombre.|
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|Recupera la cadena de valor de una métrica de evaluador de expresiones dado su nombre.|
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|Recupera el valor de una métrica con su nombre.|
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|Recupera el identificador único de una métrica con su nombre.|
|[GetMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricstring.md)|Recupera la cadena de valor de la métrica a la que se le da su nombre.|

## <a name="requirements"></a>Requisitos
Encabezado: Msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra una función que toma un **IDebugSettingsCallback2** objeto como un parámetro.

```cpp
HRESULT GetDebugSettingsCallback (IDebugSettingsCallback2 **ppCallback)
{
    HRESULT hRes = E_FAIL;

    if ( ppCallback )
    {
        if ( EVAL(m_pdec) )
            hRes = m_pdec->QueryInterface(IID_IDebugSettingsCallback2, (void **)ppCallback);
        else
            hRes = E_FAIL;
    }
    else
        hRes = E_INVALIDARG;

    return ( hRes );
}
```
