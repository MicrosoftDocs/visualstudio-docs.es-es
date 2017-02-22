---
title: "IDebugProgramProvider2::GetProviderProgramNode | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramProvider2::GetProviderProgramNode"
helpviewer_keywords: 
  - "IDebugProgramProvider2::GetProviderProgramNode"
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramProvider2::GetProviderProgramNode
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera el nodo de programa para un programa concreto.  
  
## Sintaxis  
  
```cpp  
HRESULT GetProviderProgramNode(  
   PROVIDER_FLAGS       Flags,  
   IDebugDefaultPort2*  pPort,  
   AD_PROCESS_ID        processId,  
   REFGUID              guidEngine,  
   UINT64               programId,  
   IDebugProgramNode2** ppProgramNode  
);  
```  
  
```c#  
int GetProviderProgramNode(  
   enum_PROVIDER_FLAGS    Flags,  
   IDebugDefaultPort2     pPort,  
   AD_PROCESS_ID          ProcessId,  
   ref Guid               guidEngine,  
   ulong                  programId,  
   out IDebugProgramNode2 ppProgramNode  
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
  
 `pPort`  
 \[in\]  El puerto que el proceso de llamada se ejecuta.  
  
 `processId`  
 \[in\]  Una estructura de [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) que contiene el identificador de proceso que contiene el programa en cuestión.  
  
 `guidEngine`  
 \[in\]  GUID del motor de depuración que el programa está adjunto \(si existe\).  
  
 `programId`  
 \[in\]  Identificador de programa para que obtenga el nodo del programa.  
  
 `ppProgramNode`  
 \[out\]  Un objeto de [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) que representa el nodo solicitado del programa.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [PROVIDER\_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)