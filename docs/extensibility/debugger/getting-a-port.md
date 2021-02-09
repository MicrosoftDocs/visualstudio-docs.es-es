---
title: Obtención de un puerto | Microsoft Docs
description: Obtenga información sobre cómo Visual Studio proporciona un puerto al motor de depuración para registrar nodos de programa con el puerto y para satisfacer solicitudes de información de proceso.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1f3ee9c145a4c6275f64d357d87ac1cc284bfac6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921290"
---
# <a name="get-a-port"></a>Obtener un puerto
Un puerto representa una conexión a un equipo en el que se ejecutan los procesos. Ese equipo podría ser el equipo local o un equipo remoto (que podría estar ejecutando un sistema operativo no basado en Windows; consulte [puertos](../../extensibility/debugger/ports.md) para obtener más información).

Un puerto se representa mediante la interfaz [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) . Se usa para obtener información sobre los procesos que se ejecutan en el equipo al que está conectado el puerto.

Un motor de depuración necesita acceso a un puerto para registrar los nodos del programa con el puerto y satisfacer las solicitudes de información de proceso. Por ejemplo, si el motor de depuración implementa la interfaz [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) , la implementación del método [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) podría solicitar que se devuelva la información de proceso necesaria.

Visual Studio proporciona el puerto necesario al motor de depuración y obtiene este puerto de un proveedor de puerto. Si un programa está asociado a (ya sea desde el depurador o debido a que se produjo una excepción, lo que desencadena el cuadro de diálogo Just-in-time [JIT]), el usuario recibe la opción de transporte (otro nombre para un proveedor de puerto) para su uso. De lo contrario, si el usuario inicia el programa desde el depurador, el sistema del proyecto especifica el proveedor del puerto que se va a usar. En cualquiera de los dos eventos, Visual Studio crea una instancia del proveedor del puerto, representado por una interfaz [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) , y solicita un nuevo puerto mediante una llamada a [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) con una interfaz [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) . Este puerto se pasa entonces al motor de depuración en un formulario o en otro.

## <a name="example"></a>Ejemplo
En este fragmento de código se muestra cómo usar el puerto proporcionado a [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) para registrar un nodo de programa en [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md). Los parámetros no relacionados directamente con este concepto se han omitido para mayor claridad.

> [!NOTE]
> En este ejemplo se usa el puerto para iniciar y reanudar el proceso y se supone que la interfaz [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) se implementa en el puerto. No se trata de la única forma de realizar estas tareas, y es posible que el puerto no esté implicado incluso aparte de tener el [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) del programa dado.

```cpp
// This is an IDebugEngineLaunch2 method.
HRESULT CDebugEngine::LaunchSuspended(/* omitted parameters */,
                                      IDebugPort2 *pPort,
                                      /* omitted parameters */,
                                      IDebugProcess2**ppDebugProcess)
{
    // do stuff here to set up for a launch (such as handling the other parameters)
    ...

    // Now get the IPortNotify2 interface so we can register a program node
    // in CDebugEngine::ResumeProcess.
    CComPtr<IDebugDefaultPort2> spDefaultPort;
    HRESULT hr = pPort->QueryInterface(&spDefaultPort);
    if (SUCCEEDED(hr))
    {
        CComPtr<IDebugPortNotify2> spPortNotify;
        hr = spDefaultPort->GetPortNotify(&spPortNotify);
        if (SUCCEEDED(hr))
        {
            // Remember the port notify so we can use it in ResumeProcess.
            m_spPortNotify = spPortNotify;

            // Now launch the process in a suspended state and return the
            // IDebugProcess2 interface
            CComPtr<IDebugPortEx2> spPortEx;
            hr = pPort->QueryInterface(&spPortEx);
            if (SUCCEEDED(hr))
            {
                // pass on the parameters we were given (omitted here)
                hr = spPortEx->LaunchSuspended(/* omitted parameters */,ppDebugProcess)
            }
        }
    }
    return(hr);
}

HRESULT CDebugEngine::ResumeProcess(IDebugProcess2 *pDebugProcess)
{
    // Make a program node for this process
    HRESULT hr;
    CComPtr<IDebugProgramNode2> spProgramNode;
    hr = this->GetProgramNodeForProcess(pProcess, &spProgramNode);
    if (SUCCEEDED(hr))
    {
        hr = m_spPortNotify->AddProgramNode(spProgramNode);
        if (SUCCEEDED(hr))
        {
            // resume execution of the process using the port given to us earlier.
            // (Querying for the IDebugPortEx2 interface is valid here since
            // that's how we got the IDebugPortNotify2 interface in the first place.)
            CComPtr<IDebugPortEx2> spPortEx;
            hr = m_spPortNotify->QueryInterface(&spPortEx);
            if (SUCCEEDED(hr))
            {
                hr = spPortEx->ResumeProcess(pDebugProcess);
            }
        }
    }
    return(hr);
}
```

## <a name="see-also"></a>Vea también
- [Registrar el programa](../../extensibility/debugger/registering-the-program.md)
- [Habilitar la depuración de un programa](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
- [Proveedores de puertos](../../extensibility/debugger/port-suppliers.md)
- [Puertos](../../extensibility/debugger/ports.md)
