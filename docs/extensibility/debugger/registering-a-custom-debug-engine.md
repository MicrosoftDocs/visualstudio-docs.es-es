---
title: Registro de un motor de depuración personalizado ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe6fb916810bc8a7e960a4723a6a7c7a6f0c1410
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713223"
---
# <a name="register-a-custom-debug-engine"></a>Registrar un motor de depuración personalizado
El motor de depuración debe registrarse como un generador de clases, siguiendo las convenciones COM, así como registrarse con Visual Studio a través de la subclave del Registro de Visual Studio.

> [!NOTE]
> Puede encontrar un ejemplo de cómo registrar un motor de depuración en el ejemplo TextInterpreter, que se compila como parte del Tutorial: Creación de un motor de [depuración mediante ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24).

## <a name="dll-server-process"></a>Proceso del servidor DLL
 Normalmente, un motor de depuración se configura en su propio archivo DLL como un servidor COM. Como tal, el motor de depuración debe registrar el CLSID de su generador de clases con COM antes de que Visual Studio pueda tener acceso a él. A continuación, el motor de depuración debe registrarse con Visual Studio para establecer las propiedades (también conocidas como métricas) que admite el motor de depuración. La elección de las métricas escritas en la subclave del Registro de Visual Studio depende de las características que admite el motor de depuración.

 [Las aplicaciones auxiliares](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) del SDK para la depuración describen no solo las ubicaciones del Registro necesarias para registrar un motor de depuración; también describe la biblioteca *dbgmetric.lib,* que contiene una serie de funciones y declaraciones útiles para los desarrolladores de C++ que facilitan la manipulación del registro.

### <a name="example"></a>Ejemplo
 En el ejemplo siguiente (del ejemplo TextInterpreter) se muestra cómo utilizar la `SetMetric` función (de *dbgmetric.lib*), para registrar un motor de depuración con Visual Studio. Las métricas que se pasan también se definen en *dbgmetric.lib*.

> [!NOTE]
> TextInterpreter es un motor de depuración básico; no configura (y por lo tanto no registra) ninguna otra característica. Un motor de depuración más `SetMetric` completo tendría una lista completa de llamadas o su equivalente, una para cada característica que admite el motor de depuración.

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
- [Creación de un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)
- [Ayudantes del SDK para la depuración](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Tutorial: Creación de un motor de depuración mediante ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)
