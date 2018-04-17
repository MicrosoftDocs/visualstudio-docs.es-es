---
title: Registrar el programa | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, registration
- debugging [Debugging SDK], program registration
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: febc798888cc046e514db4013edb077e25f5aaca
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="registering-the-program"></a>Registrar el programa
Después de que el motor de depuración ha adquirido un puerto, representado por un [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfaz, el paso siguiente para habilitar el programa va a depurar es registrarlo con el puerto. Una vez registrado, el programa está disponible para la depuración en uno de los siguientes medios:  
  
-   El proceso de adjuntar, que permite al depurador obtener un control completo de depuración de una aplicación en ejecución.  
  
-   Just-in-time (JIT) de depuración, que permite depurar después de hechos de un programa que se ejecuta independientemente de un depurador. Cuando la arquitectura en tiempo de ejecución detecta un error, el depurador recibe una notificación antes de que el sistema operativo o entorno en tiempo de ejecución libera la memoria y los recursos del programa con errores.  
  
## <a name="registering-procedure"></a>Registrar el procedimiento  
  
#### <a name="to-register-your-program"></a>Para registrar el programa  
  
1.  Llame a la [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) método implementado por el puerto.  
  
     `IDebugPortNotify2::AddProgramNode` requiere un puntero a un [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfaz.  
  
     Normalmente, cuando el sistema operativo o el entorno en tiempo de ejecución carga un programa, crea el nodo de programa. Si se solicita el motor de depuración (Alemania) al cargar el programa de la DE crea y registra el nodo de programa.  
  
     En el ejemplo siguiente se muestra el motor de depuración que inicie el programa y registrarlo con un puerto.  
  
    > [!NOTE]
    >  Esto no es la única manera de iniciar y reanudar un proceso; Esto es principalmente un ejemplo de registro de un programa con un puerto.  
  
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
 [Obtención de un puerto](../../extensibility/debugger/getting-a-port.md)   
 [Habilitación de un programa que se desea depurar](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)