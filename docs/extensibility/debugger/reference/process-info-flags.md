---
title: "PROCESS_INFO_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PROCESS_INFO_FLAGS"
helpviewer_keywords: 
  - "Enumeración PROCESS_INFO_FLAGS"
ms.assetid: 696951ce-701a-40c2-ac8c-b897f3aae6e2
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# PROCESS_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

describe o especifica propiedades de un proceso.  
  
## Sintaxis  
  
```cpp#  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
typedef DWORD PROCESS_INFO_FLAGS;  
```  
  
```c#  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
```  
  
## Members  
 PIFLAG\_SYSTEM\_PROCESS  
 Indica que el proceso es un proceso del sistema.  
  
 PIFLAG\_DEBUGGER\_ATTACHED  
 indica que el proceso está siendo depurado por un depurador.  Puede ser depurador de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] , o puede ser algún otro depurador, por ejemplo, WinDbg.  
  
 PIFLAG\_PROCESS\_STOPPED  
 Indica que el proceso se detiene.  Solo es válido si `PIFLAG_DEBUGGER_ATTACHED` también se especifica.  En [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)] y más adelante disponibles.  
  
 PIFLAG\_PROCESS\_RUNNING  
 Indica que el proceso se está ejecutando.  Solo es válido si `PIFLAG_DEBUGGER_ATTACHED` también se especifica.  En [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)] y más adelante disponibles.  
  
## Comentarios  
 utilizado para el miembro de `Flags` de la estructura de [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md) .  
  
 Estos marcadores se pueden combinar con `OR`bit a bit.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md)