---
title: Motor de depuración de registro personalizado | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7c87b3749c2ea63e89e2e8fb0caf773434a38df2
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44281395"
---
# <a name="register-a-custom-debug-engine"></a>Registrar un motor de depuración personalizado
El motor de depuración debe registrarse como un generador de clases siguientes convenciones de COM, así como registrar con Visual Studio a través de la subclave del registro de Visual Studio.  
  
> [!NOTE]
>  Puede encontrar un ejemplo de cómo registrar un motor de depuración en el ejemplo TextInterpreter, que se compiló como parte de la [Tutorial: creación de un motor de depuración mediante ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24).  
  
## <a name="dll-server-process"></a>Proceso de servidor DLL  
 Un motor de depuración se establece normalmente en su propio archivo DLL como servidor COM. Por lo tanto, el motor de depuración debe registrar el CLSID de su generador de clases con COM antes de Visual Studio puede tener acceso a él. A continuación, el motor de depuración debe registrarse con Visual Studio para establecer las propiedades (lo que se conoce como métricas) la depuración admite del motor. La elección de las métricas que se escriben en la subclave del registro de Visual Studio depende de las características que admite el motor de depuración.  
  
 [Aplicaciones auxiliares de SDK para la depuración](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) describe no solo las ubicaciones del registro necesarias registrar un motor de depuración; también se describe la *dbgmetric.lib* library, que contiene una serie de funciones útiles y declaraciones para los desarrolladores de C++ que hacen que manipular el registro sea más fácil.  
  
### <a name="example"></a>Ejemplo  
 El ejemplo siguiente (del ejemplo TextInterpreter) muestra cómo utilizar el `SetMetric` función (desde *dbgmetric.lib*), para registrar un motor de depuración con Visual Studio. También se definen las métricas que se pasan en *dbgmetric.lib*.  
  
> [!NOTE]
>  TextInterpreter es un motor de depuración básica; No configurado y por lo tanto, no se registra, todas las demás características. Un motor de depuración más completado tendría una lista completa de `SetMetric` llamadas o su equivalente, uno para cada característica, el motor de depuración admite.  
  
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
 [Creación de un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [Aplicaciones auxiliares de SDK para la depuración](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Tutorial: Crear un motor de depuración mediante ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)