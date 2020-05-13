---
title: IDebugProgramProvider2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2
helpviewer_keywords:
- IDebugProgramProvider2 interface
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 43557e5d81e5140967a1189e57a350595d0f7220
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721698"
---
# <a name="idebugprogramprovider2"></a>IDebugProgramProvider2
Esta interfaz registrada permite al administrador de depuración de sesión (SDM) obtener información sobre los programas que se han "publicado" a través de la [interfaz IDebugProgramPublisher2.](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)

## <a name="syntax"></a>Sintaxis

```
IDebugProgramProvider2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
El motor de depuración (DE) implementa esta interfaz para proporcionar información sobre los programas que se están depurando. Esta interfaz se registra en la sección `metricProgramProvider`DE del registro mediante la métrica , como se describe en [Aplicaciones auxiliares del SDK para la depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).

## <a name="notes-for-callers"></a>Notas para las personas que llaman
Llame a `CoCreateInstance` la función de COM con el `CLSID` proveedor del programa que se obtiene del registro. Consulte el ejemplo.

## <a name="methods-in-vtable-order"></a>Métodos en orden Vtable

|Método|Descripción|
|------------|-----------------|
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|Obtiene información sobre los programas que se ejecutan, filtrados de diversas maneras.|
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|Obtiene un nodo de programa, dado un identificador de proceso específico.|
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|Establece una devolución de llamada para observar los eventos de proveedor asociados con tipos específicos de procesos.|
|[SetLocale](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|Establece una configuración regional para los recursos específicos del idioma que necesite la DE.|

## <a name="remarks"></a>Observaciones
Normalmente, un proceso utiliza esta interfaz para averiguar acerca de los programas que se ejecutan en ese proceso.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Ejemplo

```cpp
IDebugProgramProvider2 *GetProgramProvider(GUID *pDebugEngineGuid)
{
    // This is typically defined globally. For this example, it is
    // defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugProgramProvider2 *pProvider = NULL;
    if (pDebugEngineGuid != NULL) {
        CLSID clsidProvider = { 0 };
        ::GetMetric(NULL,
                    metrictypeEngine,
                    *pDebugEngineGuid,
                    metricProgramProvider,
                    &clsidProvider,
                    strRegistrationRoot);
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {
            CComPtr<IDebugProgramProvider2> spProgramProvider;
            spProgramProvider.CoCreateInstance(clsidProvider);
            if (spProgramProvider != NULL) {
                pProvider = spProgramProvider.Detach();
            }
        }
    }
    return(pProvider);
}
```

## <a name="see-also"></a>Consulte también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [Asistentes de SDK para la depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
