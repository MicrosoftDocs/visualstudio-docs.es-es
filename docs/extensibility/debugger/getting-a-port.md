---
title: Obtención de un puerto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6c20b3e3bdc2644e7af7d9a35de06af7f96d7680
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="getting-a-port"></a>Obtención de un puerto
Un puerto representa una conexión a un equipo en el que se estén ejecutando procesos. Esa máquina podría ser el equipo local o un equipo remoto (que podría ejecutarse posiblemente un sistema operativo no basado en Windows, consulte [puertos](../../extensibility/debugger/ports.md) para obtener más información).  
  
 Un puerto representado por la [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfaz. Se utiliza para obtener información sobre los procesos que se ejecutan en el equipo que el puerto está conectado a.  
  
 Un motor de depuración necesita acceso a un puerto con el fin de registrar los nodos de programa con el puerto y satisfacer las solicitudes para obtener información de proceso. Por ejemplo, si el motor de depuración implementa la [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) de la interfaz, la implementación para la [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) método pedir el puerto para el proceso es necesario información que se devuelve.  
  
 Visual Studio proporciona el puerto necesario para el motor de depuración, y obtiene este puerto desde un proveedor de puerto. Si un programa que está asociado a (ya sea desde dentro del depurador o debido a una excepción se ha producido, lo que desencadena el cuadro de diálogo de Just-in-Time [JIT]), el usuario tiene la opción de transporte (otro nombre para un proveedor del puerto) para usar. En caso contrario, si el usuario inicia el programa desde el depurador, el sistema del proyecto especifica el proveedor del puerto a utilizar. En cualquier caso, Visual Studio crea una instancia del proveedor de puerto, representado por un [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) de interfaz y solicita un nuevo puerto mediante una llamada a [agregar puerto](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) con un [ IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) interfaz. Este puerto, a continuación, se pasa al motor de depuración en un formulario u otro.  
  
## <a name="example"></a>Ejemplo  
 Este fragmento de código muestra cómo utilizar el puerto proporcionado a [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) para registrar un nodo de programa en [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md). Parámetros no relacionados directamente con este concepto se han omitido para mayor claridad.  
  
> [!NOTE]
>  Este ejemplo utiliza el puerto para iniciar y reanudar el proceso y se da por supuesto que el [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) interfaz se implementa en el puerto. Esto no es la única forma de realizar estas tareas, y es posible que el puerto puede no incluso estar implicado distinto para que el sistema [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) especificado.  
  
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
                hr = spPortEx->LaunchSuspended(/* omitted paramters */,ppDebugProcess)  
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
                hr  = spPortEx->ResumeProcess(pDebugProcess);  
            }  
        }  
    }  
    return(hr);  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Registrar el programa](../../extensibility/debugger/registering-the-program.md)   
 [Habilitar un programa que se va a depurar](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)   
 [Proveedores de puertos](../../extensibility/debugger/port-suppliers.md)   
 [Puertos](../../extensibility/debugger/ports.md)