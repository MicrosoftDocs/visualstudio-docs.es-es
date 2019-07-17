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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205051"
---
# <a name="processinfoflags"></a>PROCESS_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Describen o especifican las propiedades de un proceso.  
  
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
 Indica que el proceso se está depurando un depurador. Puede ser un [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] depurador, o bien puede ser algún otro depurador, por ejemplo, WinDbg.  
  
 PIFLAG_PROCESS_STOPPED  
 Indica que el proceso se detiene. Sólo es válido si `PIFLAG_DEBUGGER_ATTACHED` también se especifica. Disponible en [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] y versiones posteriores.  
  
 PIFLAG_PROCESS_RUNNING  
 Indica que se está ejecutando el proceso. Sólo es válido si `PIFLAG_DEBUGGER_ATTACHED` también se especifica. Disponible en [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] y versiones posteriores.  
  
## <a name="remarks"></a>Comentarios  
 Utilizado para la `Flags` miembro de la [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) estructura.  
  
 Estas marcas se pueden combinar con un bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
