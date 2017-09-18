---
title: "AD_PROCESS_ID_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AD_PROCESS_ID_TYPE"
helpviewer_keywords: 
  - "Enumeración AD_PROCESS_ID_TYPE"
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# AD_PROCESS_ID_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica cómo interpretar un identificador de proceso en la estructura de [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) .  
  
## Sintaxis  
  
```cpp#  
enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
typedef DWORD AD_PROCESS_ID_TYPE;  
```  
  
```c#  
public enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
```  
  
## Members  
 AD\_PROCESS\_ID\_SYSTEM  
 El identificador de proceso es un identificador del sistema.  utilice el campo de `ProcessId.dwProcessId` de la estructura de [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) .  
  
 AD\_PROCESS\_ID\_GUID  
 El identificador de proceso es un GUID.  utilice el campo de `ProcessId.guidProcessId` de la estructura de `AD_PROCESS_ID` .  
  
## Comentarios  
 Utilizado para el miembro de `ProcessIdType` de la estructura de [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) para identificar el tipo de identificador de proceso que está contenido en la estructura.  determina cómo interpretar la unión de `ProcessId` en la estructura.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)