---
title: Registrar un personalizado depurar motor | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 50903d9b45828725da03c0fcb0db0f08d7f884eb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="registering-a-custom-debug-engine"></a>Registrar un motor de depuración personalizadas
El motor de depuración debe registrarse como un generador de clases según las directrices de COM, así como registrar con Visual Studio a través de la subclave del registro de Visual Studio.  
  
> [!NOTE]
>  Encontrará un ejemplo de cómo registrar un motor de depuración en el ejemplo TextInterpreter, que se genera como parte de la [Tutorial: generar una depuración motor utilizando ATL COM](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24).  
  
## <a name="dll-server-process"></a>Proceso de servidor de archivos DLL  
 Normalmente, un motor de depuración se implementa en su propio archivo DLL como un servidor COM. Esto significa que el motor de depuración debe registrar el CLSID de su generador de clases con COM para Visual Studio puede tener acceso a él. A continuación, el motor de depuración debe registrarse con Visual Studio para establecer las propiedades (lo que se conoce como métricas) la depuración admite del motor. La elección de las métricas que se escriben en la subclave del registro de Visual Studio para el motor de depuración depende de las funciones que admite el motor de depuración.  
  
 [Aplicaciones auxiliares de SDK para depuración](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) describe no solo las ubicaciones del registro necesarias para registrar un motor de depuración; también se describe la biblioteca dbgmetric.lib, que contiene una serie de funciones útiles y declaraciones para los programadores de C++ que hacen manipular el registro sea más fácil.  
  
### <a name="example"></a>Ejemplo  
 El siguiente es un ejemplo típico (del ejemplo TextInterpreter) que muestra cómo utilizar el `SetMetric` (de dbgmetric.lib), la función para registrar un motor de depuración con Visual Studio. También se definen las métricas que se pasan en dbgmetric.lib.  
  
> [!NOTE]
>  TextInterpreter es un motor de depuración básica; no implementa: y, por tanto, no se registra, todas las demás características. Un motor de depuración más completado tendría una lista completa de `SetMetric` llamadas o su equivalente, uno para cada característica, el motor de depuración es compatible con.  
  
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
 [Creación de un motor de depuración personalizadas](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [Aplicaciones auxiliares SDK para la depuración](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Tutorial: Creación de un motor de depuración mediante COM de ATL](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)