---
title: Registrando el programa | Microsoft Docs
description: Obtenga información sobre cómo un programa que se va a depurar se registra con un puerto después de que el motor de depuración adquiera un puerto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, registration
- debugging [Debugging SDK], program registration
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80c3d13cc7319e43390a7e9e6f4eb42a5a87c780
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847101"
---
# <a name="register-the-program"></a>Registrar el programa
Una vez que el motor de depuración ha adquirido un puerto, representado por una interfaz [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) , el siguiente paso para habilitar el programa que se va a depurar es registrarlo con el puerto. Una vez registrado, el programa está disponible para la depuración en uno de los siguientes medios:

- El proceso de asociar, que permite al depurador obtener el control completo de la depuración de una aplicación en ejecución.

- Depuración Just-in-Time (JIT), que permite la depuración posterior a la ejecución de un programa que se ejecuta independientemente de un depurador. Cuando la arquitectura en tiempo de ejecución detecta un error, se notifica al depurador antes de que el sistema operativo o el entorno en tiempo de ejecución libere la memoria y los recursos del programa que produce el error.

## <a name="registering-procedure"></a>Registrando procedimiento

### <a name="to-register-your-program"></a>Para registrar el programa

1. Llame al método [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) implementado por el puerto.

     `IDebugPortNotify2::AddProgramNode` requiere un puntero a una interfaz [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) .

     Normalmente, cuando el sistema operativo o el entorno de tiempo de ejecución carga un programa, crea el nodo del programa. Si se solicita al motor de depuración (DE) que cargue el programa, el crea y registra el nodo del programa.

     En el ejemplo siguiente se muestra el motor de depuración que inicia el programa y lo registra con un puerto.

    > [!NOTE]
    > Este ejemplo de código no es la única manera de iniciar y reanudar un proceso; Este código es principalmente un ejemplo de registro de un programa con un puerto.

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
- [Obtención de un puerto](../../extensibility/debugger/getting-a-port.md)
- [Habilitar la depuración de un programa](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
