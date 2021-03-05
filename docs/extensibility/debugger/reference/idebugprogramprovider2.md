---
description: Esta interfaz registrada permite que el administrador de depuración de la sesión (SDM) Obtenga información acerca de los programas que se han publicado a través de la interfaz IDebugProgramPublisher2.
title: IDebugProgramProvider2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2
helpviewer_keywords:
- IDebugProgramProvider2 interface
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d0102aa650d9739ae862f1357a1560842ae2fa59
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151446"
---
# <a name="idebugprogramprovider2"></a>IDebugProgramProvider2
Esta interfaz registrada permite que el administrador de depuración de la sesión (SDM) Obtenga información acerca de los programas que se han "publicado" a través de la interfaz [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md) .

## <a name="syntax"></a>Syntax

```
IDebugProgramProvider2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
El motor DE depuración (DE) implementa esta interfaz para proporcionar información sobre los programas que se están depurando. Esta interfaz se registra en la sección de del registro mediante la métrica `metricProgramProvider` , como se describe en [aplicaciones auxiliares de SDK para la depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).

## <a name="notes-for-callers"></a>Notas para llamadores
Llame a la `CoCreateInstance` función de com con el `CLSID` del proveedor de programas que se obtiene del registro. Vea el ejemplo.

## <a name="methods-in-vtable-order"></a>Métodos en orden vtable

|Método|Descripción|
|------------|-----------------|
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|Obtiene información acerca de los programas que se ejecutan, filtrados de varias maneras.|
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|Obtiene un nodo de programa, dado un identificador de proceso específico.|
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|Establece una devolución de llamada para inspeccionar los eventos de proveedor asociados a determinados tipos de procesos.|
|[SetLocale](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|Establece una configuración regional para los recursos específicos del idioma que necesita el DE.|

## <a name="remarks"></a>Observaciones
Normalmente, un proceso utiliza esta interfaz para obtener información acerca de los programas que se ejecutan en ese proceso.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

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
