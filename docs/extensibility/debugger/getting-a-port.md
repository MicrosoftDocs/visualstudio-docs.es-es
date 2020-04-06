---
title: Conseguir un puerto ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7bf4948e7cb2590136774eab76fbafec91dbfa40
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738636"
---
# <a name="get-a-port"></a>Obtener un puerto
Un puerto representa una conexión a una máquina en la que se ejecutan los procesos. Esa máquina podría ser la máquina local o una máquina remota (que posiblemente podría estar ejecutando un sistema operativo no basado en Windows; consulte [Puertos](../../extensibility/debugger/ports.md) para obtener más información).

Un puerto se representa mediante el [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfaz. Se utiliza para obtener información sobre los procesos que se ejecutan en la máquina a la que está conectado el puerto.

Un motor de depuración necesita acceso a un puerto para registrar los nodos de programa con el puerto y satisfacer las solicitudes de información del proceso. Por ejemplo, si el motor de depuración implementa la interfaz [IDebugProgramProvider2,](../../extensibility/debugger/reference/idebugprogramprovider2.md) la implementación del método [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) podría solicitar al puerto la información de proceso necesaria que se va a devolver.

Visual Studio proporciona el puerto necesario al motor de depuración y obtiene este puerto de un proveedor de puertos. Si se adjunta un programa (ya sea desde el depurador o debido a una excepción, que desencadena el cuadro de diálogo Just-in-Time [JIT]), se da al usuario la opción de transporte (otro nombre para un proveedor de puertos) para usar. De lo contrario, si el usuario inicia el programa desde el depurador, el sistema del proyecto especifica el proveedor de puertos que se va a utilizar. En cualquier caso, Visual Studio crea una instancia del proveedor de puertos, representado por un [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interfaz y solicita un nuevo puerto mediante una llamada a [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) con un [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) interfaz. Este puerto entonces se pasa al motor de depuración de una forma u otra.

## <a name="example"></a>Ejemplo
Este fragmento de código muestra cómo utilizar el puerto proporcionado a [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) para registrar un nodo de programa en [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md). Los parámetros no directamente relacionados con este concepto se han omitido para mayor claridad.

> [!NOTE]
> En este ejemplo se usa el puerto para iniciar y reanudar el proceso y se supone que la interfaz [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) se implementa en el puerto. Esta no es de ninguna manera la única manera de realizar estas tareas, y es posible que el puerto ni siquiera esté involucrado que no sea tener el programa [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) dado a él.

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
- [Registro del programa](../../extensibility/debugger/registering-the-program.md)
- [Habilitación de un programa que se va a depurar](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
- [Proveedores portuarios](../../extensibility/debugger/port-suppliers.md)
- [Puertos](../../extensibility/debugger/ports.md)
