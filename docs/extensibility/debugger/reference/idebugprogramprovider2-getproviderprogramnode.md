---
title: IDebugProgramProvider2::GetProviderProgramNode | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 984128fbd300a6124ea92c6fb9cb62c203a24cc2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55034629"
---
# <a name="idebugprogramprovider2getproviderprogramnode"></a>IDebugProgramProvider2::GetProviderProgramNode
Recupera el nodo de programa para un programa específico.  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
```csharp  
int GetProviderProgramNode(  
   enum_PROVIDER_FLAGS    Flags,  
   IDebugDefaultPort2     pPort,  
   AD_PROCESS_ID          ProcessId,  
   ref Guid               guidEngine,  
   ulong                  programId,  
   out IDebugProgramNode2 ppProgramNode  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Flags`  
 [in] Una combinación de marcas de la [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) enumeración. Las marcas siguientes son típicas para esta llamada:  
  
|Marcar|Descripción|  
|----------|-----------------|  
|`PFLAG_REMOTE_PORT`|Autor de la llamada se está ejecutando en el equipo remoto.|  
|`PFLAG_DEBUGGEE`|Autor de la llamada se está depurando (información adicional sobre el cálculo de referencias se devolverán para cada nodo).|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Autor de llamada se adjunta a pero no se inicia el depurador.|  
  
 `pPort`  
 [in] El puerto que el proceso de llamada se ejecuta en.  
  
 `processId`  
 [in] Un [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) estructura que contiene el identificador del proceso que contiene el programa en cuestión.  
  
 `guidEngine`  
 [in] GUID del motor de depuración que el programa está asociado a (si existe).  
  
 `programId`  
 [in] Id. del programa para la que se va a obtener el nodo de programa.  
  
 `ppProgramNode`  
 [out] Un [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objeto que representa el nodo de programa solicitado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)