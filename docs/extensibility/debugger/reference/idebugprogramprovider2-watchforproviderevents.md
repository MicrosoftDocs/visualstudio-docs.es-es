---
title: "IDebugProgramProvider2::WatchForProviderEvents | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramProvider2::WatchForProviderEvents"
helpviewer_keywords: 
  - "IDebugProgramProvider2::WatchForProviderEvents"
ms.assetid: 2eb93653-b5fb-45b6-b136-56008c5d25ef
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugProgramProvider2::WatchForProviderEvents
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Permite que el proceso es una notificación de eventos de puerto.  
  
## Sintaxis  
  
```cpp  
HRESULT WatchForProviderEvents(  
   PROVIDER_FLAGS       Flags,  
   IDebugDefaultPort2*  pPort,  
   AD_PROCESS_ID        processId,  
   CONST_GUID_ARRAY     EngineFilter,  
   REFGUID              guidLaunchingEngine,  
   IDebugPortNotify2*   pEventCallback  
);  
```  
  
```c#  
int WatchForProviderEvents(  
   enum_PROVIDER_FLAGS   Flags,  
   IDebugDefaultPort2    pPort,  
   AD_PROCESS_ID         ProcessId,  
   CONST_GUID_ARRAY      EngineFilter,  
   ref Guid              guidLaunchingEngine,  
   IDebugPortNotify2     pEventCallback  
);  
```  
  
#### Parámetros  
 `Flags`  
 \[in\]  Una combinación de marcadores de enumeración de [PROVIDER\_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) .  Los siguientes indicadores son típicos para esta llamada:  
  
|Marcador|Descripción|  
|--------------|-----------------|  
|`PFLAG_REMOTE_PORT`|El autor de llamada se ejecuta en el equipo remoto.|  
|`PFLAG_DEBUGGEE`|Están depurando al llamador actualmente \(información adicional sobre formar se devuelve para cada nodo\).|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Adjuntaron a pero no se iniciará el llamador por el depurador.|  
|`PFLAG_REASON_WATCH`|El llamador desea inspeccionar los eventos.  Si este marcador no se establece.  el evento de devolución de llamada se quita y el llamador recibe no más notificaciones.|  
  
 `pPort`  
 \[in\]  El puerto que el proceso de llamada se ejecuta.  
  
 `processId`  
 \[in\]  Una estructura de [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) que contiene el identificador de proceso que contiene el programa en cuestión.  
  
 `EngineFilter`  
 \[in\]  Una matriz de GUID de los motores de depuración asociado al proceso.  
  
 `guidLaunchingEngine`  
 \[in\]  GUID del motor de depuración que arrancó este proceso \(si existe\).  
  
 `pEventCallback`  
 \[in\]  Un objeto de [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) que recibe notificaciones de eventos.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Cuando un llamador desea quitar un controlador de eventos que se ha establecido mediante una llamada anterior a este método, el llamador pasa los mismos parámetros que realizó la primera vez pero se va del indicador de `PFLAG_REASON_WATCH` .  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo implementar este método para un objeto **de CDebugEngine** que expone la interfaz de [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) .  
  
```cpp#  
STDMETHODIMP CDebugEngine::WatchForProviderEvents(  
    PROVIDER_FLAGS Flags,   
    IDebugDefaultPort2 *pPort,   
    AD_PROCESS_ID processId,   
    CONST_GUID_ARRAY EngineFilter,   
    REFGUID guidLaunchingEngine,   
    IDebugPortNotify2 *pPortNotify)  
{  
    HRESULT hRes = E_FAIL;  
  
    if (EVAL(pPort != NULL) && EVAL(pPortNotify != NULL))  
    {  
        // We will only watch/send events about the process if the debugger  
        // is actually debugging the process, and only if this is an attach or a LoRIE launch  
        if (IsFlagSet(Flags, PFLAG_DEBUGGEE) &&  
            guidLaunchingEngine == GUID_NULL &&  
            processId.ProcessIdType == AD_PROCESS_ID_SYSTEM)  
        {  
            // We don't support WatchForProviderEvents when in interop mode  
            if (m_fInterop)  
            {  
                ASSERT(!"Shouldn't ever be called in interop mode");  
                hRes = E_FAIL;  
            }  
            else  
            {  
                if (IsFlagSet(Flags, PFLAG_REASON_WATCH))  
                {  
                    // QI to get IDebugEventCallback2 which is required.  
                    CComQIPtr<IDebugEventCallback2> pCallback(pPortNotify);  
  
                    ASSERT(pCallback != NULL);  
                    if ( pCallback != NULL )  
                    {  
                        // Register the callback  
                        hRes = this->InitDebugSession(pCallback);  
  
                        if ( S_OK == hRes )  
                        {  
                            // Get the IDebugProcess2 from the port and call AttachImpl  
                            CComPtr<IDebugProcess2> spProcess;  
  
                            hRes = pPort->GetProcess(processId, &spProcess);  
  
                            if (HREVAL(S_OK, hRes))  
                            {  
                                hRes = AttachImpl(spProcess, NULL, NULL, processId.ProcessId.dwProcessId, ATTACH_REASON_USER, NULL);  
  
                                if ( FAILED(hRes) && (!m_pPidList || 0 == m_pPidList->GetCount()) )  
                                    this->Cleanup();  
                            }  
                        }  
                        else  
                            this->Cleanup();  
                    }  
                    else  
                        hRes = E_FAIL;  
                }  
                else  
                {  
                    // Detach will be done by SDM calling on programs directly if there are managed programs.  
  
                    // This handling is the case where no managed code ever ran.  
                    if ( this->IsProcessBeingDebugged(processId.ProcessId.dwProcessId) )  
                    {  
                        ProgramList *pProgList = this->GetProgramListCopy();  
  
                        if ( EVAL(pProgList) )  
                        {  
                            if ( pProgList->GetCount() == 0)  
                            {  
                                CComPtr<ICorDebugProcess> pCorProcess;  
  
                                hRes = this->GetCorProcess(processId.ProcessId.dwProcessId, &pCorProcess);  
  
                                if (HREVAL(S_OK, hRes) )  
                                {  
                                    hRes = pCorProcess->Stop(INFINITE);  
  
                                    if ( HREVAL(S_OK, hRes) )  
                                        hRes = pCorProcess->Detach();  
                                }  
  
                                // Tell the engine that it should unregister this process from com+  
                                this->UnregisterProcess(processId.ProcessId.dwProcessId);  
  
                                // If there are no more pids left then cleanup everything.  
                                if ( 0 == m_pPidList->GetCount() )  
                                    this->Cleanup();  
                            }  
                            // This is needed for cases where the SDM has not yet recieved program create  
                            // by the time that we need to detach (example: the managed attach succeeds,  
                            // but some other attach step fails).  
                            else  
                            {  
                                PROGNODE *pProgNode = NULL;  
                                while ( pProgNode = pProgList->Next(pProgNode) )  
                                {  
                                    CDebugProgram * pProgram = ((CDebugProgram *)pProgNode->data);  
                                    hRes = pProgram->Detach();  
                                }  
                            }  
  
                            delete pProgList;  
                        }  
                    }  
                    else  
                        hRes = S_OK;  
                }  
            }  
        }  
        else  
        {  
            hRes = S_FALSE;  
        }  
    }  
    else  
    {  
        hRes = E_INVALIDARG;  
    }  
  
    return hRes;  
}  
```  
  
## Vea también  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [PROVIDER\_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [CONST\_GUID\_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)