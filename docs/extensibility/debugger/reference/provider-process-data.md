---
title: PROVIDER_PROCESS_DATA | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PROVIDER_PROCESS_DATA
helpviewer_keywords: PROVIDER_PROCESS_DATA structure
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 57b4b23f9bc723ee1ce7a10d12eb9fee0355d8ef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="providerprocessdata"></a>PROVIDER_PROCESS_DATA
Esta estructura proporciona información sobre los procesos que se ejecutan en un equipo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
typedef struct tagPROVIDER_PROCESS_DATA {  
   PROVIDER_FIELDS    Fields;  
   PROGRAM_NODE_ARRAY ProgramNodes;  
   BOOL               fIsDebuggerPresent;  
} PROVIDER_PROCESS_DATA;  
```  
  
```csharp  
public struct PROVIDER_PROCESS_DATA {  
   public uint               Fields;  
   public PROGRAM_NODE_ARRAY ProgramNodes;  
   public int                fIsDebuggerPresent;  
}  
```  
  
## <a name="members"></a>Miembros  
 Campos  
 Una combinación de indicadores de la [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md) enumeración, que indica qué campos se rellenen.  
  
 ProgramNodes  
 A [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) estructura que contiene una matriz de nodos de programa.  
  
 fIsDebuggerPresent  
 Es distinto de cero (`TRUE`) si la [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] depurador se está ejecutando, cero (`FALSE`) si no lo está.  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura se pasa a la [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) método donde se rellena.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)   
 [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)