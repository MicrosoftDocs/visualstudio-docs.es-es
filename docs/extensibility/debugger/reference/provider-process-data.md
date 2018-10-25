---
title: PROVIDER_PROCESS_DATA | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- PROVIDER_PROCESS_DATA
helpviewer_keywords:
- PROVIDER_PROCESS_DATA structure
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 789385ae229214beeb6c2ab9be90a964127e5e13
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49819737"
---
# <a name="providerprocessdata"></a>PROVIDER_PROCESS_DATA
Esta estructura proporciona información acerca de los procesos que se ejecutan en una máquina.  
  
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
 Una combinación de marcas de la [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md) enumeración, que indica qué campos se rellenan.  
  
 ProgramNodes  
 Un [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) estructura que contiene una matriz de nodos de programa.  
  
 fIsDebuggerPresent  
 Distinto de cero (`TRUE`) si el [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] depurador se está ejecutando, cero (`FALSE`) si no lo está.  
  
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