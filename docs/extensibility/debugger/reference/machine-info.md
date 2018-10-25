---
title: MACHINE_INFO | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- MACHINE_INFO
helpviewer_keywords:
- MACHINE_INFO structure
ms.assetid: e7564ff2-00b5-4750-8fd5-dc1029a16912
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e548552b5acda6a3334b6d7df90b2aeab80c2e77
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847232"
---
# <a name="machineinfo"></a>MACHINE_INFO
Describe un equipo determinado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
typedef struct tagMACHINE_INFO {   
   MACHINE_INFO_FIELDS Fields;  
   BSTR                bstrName;  
   MACHINE_INFO_FLAGS  Flags;  
} MACHINE_INFO;  
```  
  
```csharp  
public struct MACHINE_INFO {   
   public uint   Fields;  
   public string bstrName;  
   public uint   Flags;  
};  
```  
  
## <a name="members"></a>Miembros  
 `Fields`  
 Una combinación de marcas de la [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) enumeración que especifican qué campos de la estructura se inicializan.  
  
 `bstrName`  
 El nombre del equipo. Equivalente a llamar a [GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md).  
  
 `Flags`  
 Una combinación de marcas de la [MACHINE_INFO_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md) enumeración que describe los atributos de la máquina.  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura es devuelto por una llamada a la [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)   
 [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)