---
title: "MODULE_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MODULE_FLAGS"
helpviewer_keywords: 
  - "Enumeración MODULE_FLAGS"
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# MODULE_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Se utiliza para describir un módulo.  
  
## Sintaxis  
  
```cpp#  
enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
typedef DWORD MODULE_FLAGS;  
```  
  
```c#  
public enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
```  
  
## Members  
 MODULE\_FLAG\_NONE  
 no especifica ningún módulo.  
  
 MODULE\_FLAG\_SYSTEM  
 especifica un módulo de sistema.  
  
 MODULE\_FLAG\_SYMBOLS  
 Especifica un módulo de símbolos.  
  
 MODULE\_FLAG\_64BIT  
 Especifica un módulo de 64 bits.  
  
 MODULE\_FLAG\_OPTIMIZED  
 especifica el módulo se ha optimizado.  Reflejan a este estado en la ventana de **Módulos** .  
  
 MODULE\_FLAG\_UNOPTIMIZED  
 especifica el módulo no se ha optimizado.  Reflejan a este estado en la ventana de **Módulos** .  Es el estado predeterminado.  
  
## Comentarios  
 utilizado para el miembro de `m_dwModuleFlags` de la estructura de [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) .  
  
 Estos marcadores se pueden combinar con `OR`bit a bit.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)