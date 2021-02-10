---
title: Registrando un motor de depuración personalizado | Microsoft Docs
description: Obtenga información sobre cómo el motor de depuración se registra como un generador de clases, siguiendo las convenciones de COM, así como el registro con Visual Studio a través del registro.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4581411a2601bf598762a7157f9df0e006995230
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961123"
---
# <a name="register-a-custom-debug-engine"></a>Registrar un motor de depuración personalizado
El motor de depuración debe registrarse como un generador de clases, siguiendo las convenciones de COM y registrarse con Visual Studio a través de la subclave del registro de Visual Studio.

> [!NOTE]
> Puede encontrar un ejemplo de cómo registrar un motor de depuración en el ejemplo TextInterpreter, que se genera como parte del [Tutorial: compilar un motor de depuración con ATL com](/previous-versions/bb147024(v=vs.90)).

## <a name="dll-server-process"></a>Proceso de servidor DLL
 Normalmente, un motor de depuración se configura en su propio archivo DLL como un servidor COM. Como tal, el motor de depuración debe registrar el CLSID de su generador de clases con COM para que Visual Studio pueda acceder a él. Después, el motor de depuración debe registrarse con Visual Studio para establecer las propiedades (también conocidas como métricas) que admite el motor de depuración. La elección de las métricas escritas en la subclave del registro de Visual Studio depende de las características que admite el motor de depuración.

 Las [aplicaciones auxiliares de SDK para la depuración](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) describen no solo las ubicaciones del registro necesarias para registrar un motor de depuración; también se describe la biblioteca *dbgmetric. lib* , que contiene una serie de funciones y declaraciones útiles para los desarrolladores de C++ que facilitan la manipulación del registro.

### <a name="example"></a>Ejemplo
 En el ejemplo siguiente (del ejemplo TextInterpreter) se muestra cómo usar la `SetMetric` función (de *dbgmetric. lib*) para registrar un motor de depuración con Visual Studio. Las métricas que se pasan también se definen en *dbgmetric. lib*.

> [!NOTE]
> TextInterpreter es un motor de depuración básico; no se configura (y, por lo tanto, no se registra) ninguna otra característica. Un motor de depuración más completo tendría una lista completa de `SetMetric` llamadas o su equivalente, una para cada característica que el motor de depuración admite.

```
// Define base registry subkey to Visual Studio.
static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0";

HRESULT CTextInterpreterModule::RegisterServer(BOOL bRegTypeLib, const CLSID * pCLSID)
{
    SetMetric(metrictypeEngine, __uuidof(Engine), metricName, L"Text File", false, strRegistrationRoot);
    SetMetric(metrictypeEngine, __uuidof(Engine), metricCLSID, CLSID_Engine, false, strRegistrationRoot);
    SetMetric(metrictypeEngine, __uuidof(Engine), metricProgramProvider, CLSID_MsProgramProvider, false, strRegistrationRoot);

    return base::RegisterServer(bRegTypeLib, pCLSID);
}
```

## <a name="see-also"></a>Vea también
- [Crear un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)
- [Aplicaciones auxiliares de SDK para depuración](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Tutorial: crear un motor de depuración mediante ATL COM](/previous-versions/bb147024(v=vs.90))