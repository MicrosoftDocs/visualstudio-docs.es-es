---
title: "IDebugProgramProvider2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramProvider2"
helpviewer_keywords: 
  - "Interfaz IDebugProgramProvider2"
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugProgramProvider2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz registrada permite que el administrador de depuración de la sesión \(SDM\) para obtener información sobre los programas que “se han publicado” a través de la interfaz de [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md) .  
  
## Sintaxis  
  
```  
IDebugProgramProvider2 : IUnknown  
```  
  
## Notas para los implementadores  
 El motor de depuración \(DE\) implementa esta interfaz para proporcionar información sobre los programas que se están depurando.  Esta interfaz se registra en el OF section de registro mediante `metricProgramProvider`métrica, como se describe en [Aplicaciones auxiliares SDK para la depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).  
  
## Notas para los llamadores  
 Función de `CoCreateInstance` de COM de llamada con `CLSID` de proveedor del programa se obtiene del registro.  Vea el ejemplo.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|Obtiene información sobre los programas que se ejecutan, filtrado de diversas maneras.|  
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|Obtiene un nodo de programa, dado un identificador de proceso concreto|  
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|Establece una devolución de llamada para inspeccionar los eventos del proveedor asociado a clases específicas de procesos.|  
|[SetLocale](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|Establece una configuración regional para cualquier recurso concreto de idioma necesario por el OF.|  
  
## Comentarios  
 Normalmente, un proceso utiliza esta interfaz para obtener información sobre los programas que se ejecutan en ese proceso.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Ejemplo  
  
```cpp#  
IDebugProgramProvider2 *GetProgramProvider(GUID *pDebugEngineGuid)  
{  
    // This is typically defined globally.  For this example, it is  
    // defined here.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
    IDebugProgramProvider2 *pProvider = NULL;  
    if (pDebugEngineGuid != NULL) {  
        CLSID clsidProvider = { 0 };  
        ::GetMetric(NULL,  
                    metrictypeEngine,  
                    *pDebugEngineGuid,  
                    metricProgramProvider,  
                    &clsidProvider,  
                    strRegistrationRoot);  
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {  
            CComPtr<IDebugProgramProvider2> spProgramProvider;  
            spProgramProvider.CoCreateInstance(clsidProvider);  
            if (spProgramProvider != NULL) {  
                pProvider = spProgramProvider.Detach();  
            }  
        }  
    }  
    return(pProvider);  
}  
```  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [Aplicaciones auxiliares SDK para la depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)