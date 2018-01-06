---
title: PROVIDER_FLAGS | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PROVIDER_FLAGS
helpviewer_keywords: PROVIDER_FLAGS enumeration
ms.assetid: 8cbd2312-ed2f-4477-b192-c3f25c6098c3
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f6f2a1b57c627425ebf63c6068f358cb8be0d3c1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="providerflags"></a>PROVIDER_FLAGS
Especifica las propiedades deseadas a obtenerse a partir de un proveedor de programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_PROVIDER_FLAGS {  
   PFLAG_NONE                    = 0x00,  
   PFLAG_REMOTE_PORT             = 0x01,  
   PFLAG_DEBUGGEE                = 0x02,  
   PFLAG_ATTACHED_TO_DEBUGGEE    = 0x04,  
   PFLAG_REASON_WATCH            = 0x08,  
   PFLAG_GET_PROGRAM_NODES       = 0x10,  
   PFLAG_GET_IS_DEBUGGER_PRESENT = 0x20  
};  
typedef DWORD PROVIDER_FLAGS;  
```  
  
```csharp  
public enum enum_PROVIDER_FLAGS {  
   PFLAG_NONE                    = 0x00,  
   PFLAG_REMOTE_PORT             = 0x01,  
   PFLAG_DEBUGGEE                = 0x02,  
   PFLAG_ATTACHED_TO_DEBUGGEE    = 0x04,  
   PFLAG_REASON_WATCH            = 0x08,  
   PFLAG_GET_PROGRAM_NODES       = 0x10,  
   PFLAG_GET_IS_DEBUGGER_PRESENT = 0x20  
};  
```  
  
## <a name="members"></a>Miembros  
 PFLAG_NONE  
 No existen marcadores especificados.  
  
 PFLAG_REMOTE_PORT  
 Llamador quiere una lista de programas en un equipo diferente que [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].  
  
 PFLAG_DEBUGGEE  
 Se está depurando el proceso de esta instancia de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].  
  
 PFLAG_ATTACH_TODEBUGGEE  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]se adjunta al programa que se está depurando, pero no se inició.  
  
 PFLAG_REASON_WATCH  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]está viendo eventos.  
  
 PFLAG_GET_PROGRAM_NODES  
 Llamador quiere la `ProgramNodes` campo de la [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) estructura.  
  
 PFLAG_GET_IS_DEBUGGER_PRESENT  
 Llamador quiere la `fIsTheDebuggerPresent` campo de la `PROVIDER_PROCESS_DATA` estructura.  
  
## <a name="remarks"></a>Comentarios  
 Estas marcas se pasan a los métodos siguientes:  
  
-   [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)  
  
-   [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)  
  
-   [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)  
  
 Estos valores se pueden combinar con un bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)   
 [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)