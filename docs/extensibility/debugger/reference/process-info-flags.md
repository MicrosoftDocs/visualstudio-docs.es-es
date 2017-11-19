---
title: PROCESS_INFO_FLAGS | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PROCESS_INFO_FLAGS
helpviewer_keywords: PROCESS_INFO_FLAGS enumeration
ms.assetid: 696951ce-701a-40c2-ac8c-b897f3aae6e2
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 228b2d3286ad0b69a2eb813e18b8837ec038f28f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="processinfoflags"></a>PROCESS_INFO_FLAGS
Describe las o especifica las propiedades de un proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
typedef DWORD PROCESS_INFO_FLAGS;  
```  
  
```csharp  
enum enum_PROCESS_INFO_FLAGS {   
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
 Indica que el proceso se está depurando un depurador. Puede ser un [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] depurador, o puede ser algún otro depurador, por ejemplo, WinDbg.  
  
 PIFLAG_PROCESS_STOPPED  
 Indica que el proceso se detiene. Sólo es válido si `PIFLAG_DEBUGGER_ATTACHED` también se especifica. Disponible en [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)] y versiones posteriores.  
  
 PIFLAG_PROCESS_RUNNING  
 Indica que el proceso se está ejecutando. Sólo es válido si `PIFLAG_DEBUGGER_ATTACHED` también se especifica. Disponible en [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)] y versiones posteriores.  
  
## <a name="remarks"></a>Comentarios  
 Utilizado para la `Flags` miembro de la [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) estructura.  
  
 Estas marcas se pueden combinar con un bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)