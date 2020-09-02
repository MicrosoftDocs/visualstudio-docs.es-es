---
title: Registrando un motor de depuración personalizado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9cf06e881034b980b8e40e095779007b3c7fa6f6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703606"
---
# <a name="registering-a-custom-debug-engine"></a>Registro de un motor de depuración personalizado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El motor de depuración debe registrarse como un generador de clases según las convenciones de COM y registrarse en Visual Studio a través de la subclave del registro de Visual Studio.  
  
> [!NOTE]
> Un ejemplo de cómo registrar un motor de depuración se puede encontrar en el ejemplo TextInterpreter, que se genera como parte del [Tutorial: compilar un motor de depuración con ATL com](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24).  
  
## <a name="dll-server-process"></a>Proceso de servidor DLL  
 Normalmente, un motor de depuración se implementa en su propio archivo DLL como un servidor COM. Esto significa que el motor de depuración debe registrar el CLSID de su generador de clases con COM para que Visual Studio pueda acceder a él. Después, el motor de depuración debe registrarse con Visual Studio para establecer las propiedades (también conocidas como métricas) que admite el motor de depuración. La elección de las métricas que se escriben en la subclave del registro de Visual Studio para el motor de depuración depende de las características que admite el motor de depuración.  
  
 Las [aplicaciones auxiliares de SDK para la depuración](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) describen no solo las ubicaciones del registro necesarias para registrar un motor de depuración; también se describe la biblioteca dbgmetric. lib, que contiene una serie de funciones y declaraciones útiles para los desarrolladores de C++ que facilitan la manipulación del registro.  
  
### <a name="example"></a>Ejemplo  
 A continuación se muestra un ejemplo típico (del ejemplo TextInterpreter) que muestra cómo usar la `SetMetric` función (de dbgmetric. lib) para registrar un motor de depuración con Visual Studio. Las métricas que se pasan también se definen en dbgmetric. lib.  
  
> [!NOTE]
> TextInterpreter es un motor de depuración básico; no implementa y, por lo tanto, no registra ninguna otra característica. Un motor de depuración más completo tendría una lista completa de `SetMetric` llamadas o su equivalente, una para cada característica que el motor de depuración admite.  
  
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
  
## <a name="see-also"></a>Consulte también  
 [Crear un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [Aplicaciones auxiliares de SDK para depuración](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Tutorial: crear un motor de depuración mediante ATL COM](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)
