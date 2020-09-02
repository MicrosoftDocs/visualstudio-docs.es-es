---
title: PROCESS_INFO_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
ms.assetid: 696951ce-701a-40c2-ac8c-b897f3aae6e2
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 88ff2a1da1f937fd4011932979bd95057eb40dfd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205051"
---
# <a name="process_info_flags"></a>PROCESS_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Describe o especifica las propiedades de un proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
typedef DWORD PROCESS_INFO_FLAGS;  
```  
  
```csharp  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
```  
  
## <a name="members"></a>Miembros  
 PIFLAG_SYSTEM_PROCESS  
 Indica que el proceso es un proceso del sistema.  
  
 PIFLAG_DEBUGGER_ATTACHED  
 Indica que un depurador está depurando el proceso. Puede ser un [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] depurador o puede ser algún otro depurador, por ejemplo, WinDbg.  
  
 PIFLAG_PROCESS_STOPPED  
 Indica que el proceso está detenido. Solo es válido si `PIFLAG_DEBUGGER_ATTACHED` también se especifica. Disponible en [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] y versiones posteriores.  
  
 PIFLAG_PROCESS_RUNNING  
 Indica que el proceso se está ejecutando. Solo es válido si `PIFLAG_DEBUGGER_ATTACHED` también se especifica. Disponible en [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] y versiones posteriores.  
  
## <a name="remarks"></a>Observaciones  
 Se utiliza para el `Flags` miembro de la estructura [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) .  
  
 Estas marcas se pueden combinar con una operación bit a bit `OR` .  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
