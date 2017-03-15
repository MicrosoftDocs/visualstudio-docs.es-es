---
title: "Registrar el programa | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "programas, registro"
  - "depurar [SDK de depuración], programar el registro"
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Registrar el programa
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Después de que el motor de depuración haya adquirido un puerto, representado por una interfaz de [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) , el paso siguiente de habilitar el programa que se va a depurar es registrarlo con el puerto.  Una vez registrado, el programa está disponible para depurar por uno de los siguientes significa:  
  
-   El proceso de asociación, que permite al depurador permite completa el control de depuración de una aplicación en ejecución.  
  
-   Depuración \(JIT\) Just\-In\-Time, que permite la depuración de después \-\- hecho de un programa que se ejecuta independientemente de un depurador.  Cuando la arquitectura en tiempo de ejecución detecta un error, notifica al depurador antes de las versiones del entorno del sistema operativo o de tiempo de ejecución memoria y recursos del error.  
  
## registrar procedimiento  
  
#### para registrar el programa  
  
1.  Llame al método de [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) implementado por el puerto.  
  
     `IDebugPortNotify2::AddProgramNode` requiere un puntero a una interfaz de [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) .  
  
     Normalmente, cuando el sistema operativo o el entorno de tiempo de ejecución carga un programa, crea el nodo del programa.  Si el motor de depuración \(DE\) se pide cargar el programa el OF crea y registra el nodo del programa.  
  
     El ejemplo siguiente se muestra el motor de depuración que inicia el programa y que se registra con un puerto.  
  
    > [!NOTE]
    >  Ésta no es la única manera de iniciar y reanudación de un proceso; éste es principalmente un ejemplo de registrar un programa con un puerto.  
  
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
 [Obtención de un puerto](../../extensibility/debugger/getting-a-port.md)   
 [Habilitación de un programa que se desea depurar](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)