---
title: "Registrar un motor de depuraci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "motores de depuración, registrar"
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# Registrar un motor de depuraci&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El motor de depuración debe registrarse como un generador de clases que siguen las convenciones de COM, así como registrar con Visual Studio a través de la subclave del registro de Visual Studio.  
  
> [!NOTE]
>  Encontrará un ejemplo de cómo registrar un motor de depuración en el ejemplo TextInterpreter, que se genera como parte de la [Tutorial: Building a Debug Engine Using ATL COM](http://msdn.microsoft.com/es-es/9097b71e-1fe7-48f7-bc00-009e25940c24).  
  
## Proceso de servidor de DLL  
 Normalmente, un motor de depuración se implementa en su propio archivo DLL como un servidor COM. Esto significa que el motor de depuración debe registrar el CLSID de su generador de clases con COM antes de Visual Studio puede tener acceso a él. A continuación, el motor de depuración debe registrarse con el propio Visual Studio para establecer las propiedades \(lo que se conoce como métricas\) la depuración admite el motor. La elección de métricas que se escriben en la subclave del registro de Visual Studio para el motor de depuración depende de las características que admite el motor de depuración.  
  
 [Aplicaciones auxiliares SDK para la depuración](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) Describe no sólo las ubicaciones del registro necesarias para registrar un motor de depuración; También describe la biblioteca dbgmetric.lib, que contiene un número de funciones útiles y declaraciones para desarrolladores de C\+\+ que hacen de manipular el registro más fácil.  
  
### Ejemplo  
 El siguiente es un ejemplo típico \(del ejemplo TextInterpreter\) que muestran cómo utilizar el `SetMetric` función \(de dbgmetric.lib\), para registrar un motor de depuración con Visual Studio. También se definen las métricas que se pasan en dbgmetric.lib.  
  
> [!NOTE]
>  TextInterpreter es un motor de depuración básica; no implementa — y, por tanto, no se registra, todas las demás características. Un motor de depuración más completado tendría una lista completa de `SetMetric` llamadas o su equivalente, uno para cada característica de motor de depuración admite.  
  
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
  
## Vea también  
 [Creación de un motor de depuración](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [Aplicaciones auxiliares SDK para la depuración](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Tutorial: Building a Debug Engine Using ATL COM](http://msdn.microsoft.com/es-es/9097b71e-1fe7-48f7-bc00-009e25940c24)