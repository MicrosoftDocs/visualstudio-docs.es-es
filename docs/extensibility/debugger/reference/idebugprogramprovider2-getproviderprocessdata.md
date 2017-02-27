---
title: "IDebugProgramProvider2::GetProviderProcessData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramProvider2::GetProviderProcessData"
helpviewer_keywords: 
  - "IDebugProgramProvider2::GetProviderProcessData"
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugProgramProvider2::GetProviderProcessData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

recupera una lista de programas en ejecución de un proceso especificado.  
  
## Sintaxis  
  
```cpp  
HRESULT GetProviderProcessData(  
   PROVIDER_FLAGS         Flags,  
   IDebugDefaultPort2*    pPort,  
   AD_PROCESS_ID          processId,  
   CONST_GUID_ARRAY       EngineFilter,  
   PROVIDER_PROCESS_DATA* pProcess  
);  
```  
  
```c#  
int GetProviderProcessData(  
   enum_PROVIDER_FLAGS     Flags,  
   IDebugDefaultPort2      pPort,  
   AD_PROCESS_ID           ProcessId,  
   CONST_GUID_ARRAY        EngineFilter,  
   PROVIDER_PROCESS_DATA[] pProcess  
);  
```  
  
#### Parámetros  
 `Flags`  
 \[in\]  Una combinación de marcadores de enumeración de [PROVIDER\_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) .  Los siguientes indicadores son típicos para esta llamada:  
  
|Marcador|Descripción|  
|--------------|-----------------|  
|`PFLAG_REMOTE_PORT`|El autor de llamada se ejecuta en el equipo remoto.|  
|`PFLAG_DEBUGGEE`|Están depurando al llamador actualmente \(información adicional sobre formar será devuelta para cada nodo\).|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Adjuntaron a pero no se iniciará el llamador por el depurador.|  
|`PFLAG_GET_PROGRAM_NODES`|El llamador es ordenar una lista de nodos de programa devolverse.|  
  
 `pPort`  
 \[in\]  El puerto que el proceso de llamada se ejecuta.  
  
 `processId`  
 \[in\]  Una estructura de [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) que contiene el identificador de proceso que contiene el programa en cuestión.  
  
 `EngineFilter`  
 \[in\]  Una matriz de GUID para los motores de depuración asignados para depurar este proceso \(se utilizarán para filtrar los programas que realmente se devuelven según lo que compatibilidad con motores proporcionado; si no se especifica ningún motores, después todos los programas se devolverá\).  
  
 `pProcess`  
 \[out\]  Una estructura de [PROVIDER\_PROCESS\_DATA](../../../extensibility/debugger/reference/provider-process-data.md) que se rellena con la información solicitada.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Este método llama normalmente por un proceso para obtener una ejecución de la lista de programas en ese proceso.  la información devuelta es una lista de objetos de [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) .  
  
## Vea también  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [CONST\_GUID\_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)   
 [PROVIDER\_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [PROVIDER\_PROCESS\_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)