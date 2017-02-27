---
title: "Obtenci&#243;n de un puerto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "puertos, introducción"
  - "depurar [SDK de depuración], puertos"
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Obtenci&#243;n de un puerto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un puerto representa una conexión a un equipo en el que los procesos se están ejecutando.  Ese equipo podría ser el equipo local o en un equipo remoto \(que podrían ejecutar posiblemente un sistema operativo no\-Windows\-basado; vea [Puertos](../../extensibility/debugger/ports.md) para obtener más información\).  
  
 Un puerto se representa mediante la interfaz de [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) .  Se usa para obtener información sobre los procesos que se ejecutan en el equipo que el puerto está conectado con.  
  
 Un motor de depuración necesita acceso a un puerto para registrar nodos de programa al puerto y satisfacer las solicitudes información de proceso.  Por ejemplo, si el motor de depuración implementa la interfaz de [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) , la implementación del método de [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) podría pedir al puerto información de proceso necesaria es devuelto.  
  
 Fuentes de Visual Studio el puerto necesario al motor de depuración, y se obtiene este puerto de un proveedor de puerto.  Si se asocia un programa \(dentro del depurador o debido a una excepción se inició, que desencadena el cuadro de diálogo just\-in\-time \[JIT\]\), ofrecen el usuario la opción de transporte \(otro nombre para un proveedor de puerto\) a utilizar.  Si no, si el usuario inicia el programa dentro del depurador, el sistema del proyecto especifica el proveedor de puerto para utilizar.  En cualquier evento, Visual Studio crea instancias del proveedor de puerto, representado por una interfaz de [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) , y solicita un nuevo puerto llamando a [Agregar puerto](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) con una interfaz de [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) .  Este puerto se pasa al motor de depuración de una forma u otra.  
  
## Ejemplo  
 Este fragmento de código se muestra cómo utilizar el puerto proporcionado a [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) para registrar un nodo de programa en [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md).  Los parámetros relacionados no directamente con este concepto se han omitido para mayor claridad.  
  
> [!NOTE]
>  Este ejemplo utiliza el puerto para iniciar y reanudar el proceso y se supone que la interfaz de [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) se implementa en el puerto.  Ésta es de ninguna manera la única forma de realizar estas tareas, y es posible que el puerto puede ni siquiera estar implicado distinto tener [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) del especificado al.  
  
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
  
## Vea también  
 [Registrar el programa](../../extensibility/debugger/registering-the-program.md)   
 [Habilitación de un programa que se desea depurar](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)   
 [Proveedores de puertos](../../extensibility/debugger/port-suppliers.md)   
 [Puertos](../../extensibility/debugger/ports.md)