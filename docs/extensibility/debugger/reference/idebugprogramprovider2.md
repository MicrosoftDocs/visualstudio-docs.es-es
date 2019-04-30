---
title: IDebugProgramProvider2 | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2
helpviewer_keywords:
- IDebugProgramProvider2 interface
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74604e0b3446e33962c6a8e69a69bfc400f0e3e2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916702"
---
# <a name="idebugprogramprovider2"></a>IDebugProgramProvider2
Esta interfaz registrada permite la depuración de la sesión manager (SDM) para obtener información acerca de los programas que se han "publicado" a través de la [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md) interfaz.

## <a name="syntax"></a>Sintaxis

```
IDebugProgramProvider2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
El motor de depuración (DE) implementa esta interfaz para proporcionar información acerca de los programas que se está depurando. Esta interfaz está registrada en la sección del registro con la métrica `metricProgramProvider`, tal y como se describe en [aplicaciones auxiliares de SDK para depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).

## <a name="notes-for-callers"></a>Notas para los llamadores
Llame a la de COM `CoCreateInstance` funcionando con el `CLSID` del proveedor de programa que se obtiene del registro. Vea el ejemplo.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable

|Método|Descripción|
|------------|-----------------|
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|Obtiene información acerca de los programas que está ejecutando, el filtrado en una variedad de formas.|
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|Obtiene un nodo de programa, dado un identificador de proceso específico.|
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|Establece una devolución de llamada para inspeccionar los eventos del proveedor asociados con determinados tipos de procesos.|
|[SetLocale](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|Establece una configuración regional para los recursos específicos del idioma necesarios para la DE.|

## <a name="remarks"></a>Comentarios
Normalmente, un proceso usa esta interfaz para obtener información sobre los programas que se ejecutan en ese proceso.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

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

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [Asistentes de SDK para la depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
