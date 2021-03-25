---
description: Permite a los motores de depuración leer la configuración de métricas de forma remota.
title: IDebugSettingsCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2 interface
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 58e9ddfd3789fcfe7d81348714a8de2add743090
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071199"
---
# <a name="idebugsettingscallback2"></a>IDebugSettingsCallback2
Permite a los motores de depuración leer la configuración de métricas de forma remota.

## <a name="syntax"></a>Sintaxis

```
IDebugSettingsCallback2D : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
Esta interfaz se implementa mediante la devolución de llamada de evento del administrador de depuración de sesión y la utilizan los motores de depuración. También podría usarse localmente en lugar de Dbgmetric [d]. lib.

## <a name="methods"></a>Métodos
En la tabla siguiente se muestran los métodos de `IDebugSettingsCallback2` .

|Método|Descripción|
|------------|-----------------|
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|Enumera los evaluadores de expresiones disponibles a partir de los identificadores de idioma y proveedor.|
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|Recupera un objeto local del evaluador de expresiones según la métrica.|
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|Recupera un valor que corresponde a la métrica especificada del evaluador de expresiones.|
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|Recupera el archivo de métrica del evaluador de expresiones dado el nombre o la métrica.|
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|Recupera el identificador único para una métrica del evaluador de expresiones a partir de su nombre.|
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|Recupera la cadena de valor de una métrica del evaluador de expresiones a partir de su nombre.|
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|Recupera el valor de una métrica dado su nombre.|
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|Recupera el identificador único de una métrica dado su nombre.|
|[GetMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricstring.md)|Recupera la cadena de valor de la métrica a partir de su nombre.|

## <a name="requirements"></a>Requisitos
Encabezado: Msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra una función que toma un objeto **IDebugSettingsCallback2** como parámetro.

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
