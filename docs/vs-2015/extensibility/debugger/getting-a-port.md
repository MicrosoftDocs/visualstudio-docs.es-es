---
title: Obtención de un puerto | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 660ead58af40f85b4da4d68d7172866f5fe1fd0c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789907"
---
# <a name="getting-a-port"></a>Obtención de un puerto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un puerto representa una conexión a un equipo en el que se estén ejecutando procesos. Esa máquina puede ser el equipo local o un equipo remoto (que podría ejecutarse, posiblemente, un sistema operativo no basado en Windows; vea [puertos](../../extensibility/debugger/ports.md) para obtener más información).  
  
 Un puerto representado por la [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfaz. Sirve para obtener información sobre los procesos que se ejecutan en el equipo en a que el puerto está conectado.  
  
 Un motor de depuración necesita acceso a un puerto con el fin de registrar los nodos de programa con el puerto así como para satisfacer las solicitudes de información de proceso. Por ejemplo, si el motor de depuración implementa el [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) interfaz, la implementación para el [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) método podría pedir el puerto para el proceso necesario información que se devuelve.  
  
 Visual Studio proporciona el puerto necesario para el motor de depuración, y obtiene este puerto de un proveedor de puerto. Si un programa que está asociado a (ya sea de dentro del depurador o debido a una excepción se inicia, lo que desencadena el cuadro de diálogo Just-in-Time [JIT]), el usuario tiene la opción de transporte (otro nombre para un proveedor de puerto) para usar. En caso contrario, si el usuario inicia el programa desde el depurador, el sistema del proyecto especifica el proveedor del puerto a utilizar. En cualquier caso, Visual Studio crea una instancia de proveedor del puerto, representado por un [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interfaz y solicita un nuevo puerto mediante una llamada a [agregar puerto](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) con un [ IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) interfaz. Este puerto, a continuación, se pasa al motor de depuración en un formulario u otro.  
  
## <a name="example"></a>Ejemplo  
 Este fragmento de código muestra cómo usar el puerto proporcionado a [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) para registrar un nodo de programa en [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md). Los parámetros no directamente relacionados con este concepto se han omitido para mayor claridad.  
  
> [!NOTE]
>  En este ejemplo usa el puerto para iniciar y reanudar el proceso y se da por supuesto que el [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) interfaz se implementa en el puerto. Esto no es la única forma de realizar estas tareas, y es posible que el puerto puede no incluso participar distinto que el programa [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) que le asignó.  
  
```cpp#  
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
                hr  = spPortEx->ResumeProcess(pDebugProcess);  
            }  
        }  
    }  
    return(hr);  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Registro del programa](../../extensibility/debugger/registering-the-program.md)   
 [Habilitación de un programa que se desea depurar](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)   
 [Proveedores de puertos](../../extensibility/debugger/port-suppliers.md)   
 [Puertos](../../extensibility/debugger/ports.md)

