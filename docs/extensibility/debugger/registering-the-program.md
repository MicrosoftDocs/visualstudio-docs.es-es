---
title: Registro del programa | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, registration
- debugging [Debugging SDK], program registration
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d517e973ed712e7d3cbbacde482fdf7030ffc81e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55006286"
---
# <a name="register-the-program"></a>Registrar el programa
Después de que el motor de depuración ha adquirido un puerto, representado por un [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfaz, que es el paso siguiente para habilitar el programa que se desea depurar registrarlo en el puerto. Una vez registrado, el programa está disponible para la depuración en uno de los siguientes medios:  
  
-   El proceso de adjuntar, lo que permite al depurador que obtenga un control total de depuración de una aplicación en ejecución.  
  
-   Just-in-time (JIT) de depuración, lo que permite la depuración después de los hechos de un programa que se ejecuta independientemente de un depurador. Cuando la arquitectura en tiempo de ejecución detecta un error, se notifica el depurador antes de que el sistema operativo o el entorno de tiempo de ejecución libera la memoria y los recursos del programa con errores.  
  
## <a name="registering-procedure"></a>Registro de procedimiento  
  
### <a name="to-register-your-program"></a>Para registrar el programa  
  
1.  Llame a la [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) método implementado por el puerto.  
  
     `IDebugPortNotify2::AddProgramNode` requiere un puntero a un [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfaz.  
  
     Normalmente, cuando un programa se carga el sistema operativo o el entorno de tiempo de ejecución, crea el nodo del programa. Si se solicita el motor de depuración (DE) para cargar el programa, la DE crea y registra el nodo del programa.  
  
     El ejemplo siguiente muestra el motor de depuración, iniciar el programa y registrarlo con un puerto.  
  
    > [!NOTE]
    >  Este ejemplo de código no es la única forma de iniciar y reanudar un proceso; Este código es principalmente un ejemplo de registro de un programa con un puerto.  
  
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