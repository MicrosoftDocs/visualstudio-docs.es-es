---
title: "ASSEMBLYLOCRESOLUTION | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ASSEMBLYLOCRESOLUTION"
helpviewer_keywords: 
  - "Enumeración ASSEMBLYLOCRESOLUTION"
ms.assetid: 0bcfe85c-5f37-4a9d-bf2b-141acd96ad67
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# ASSEMBLYLOCRESOLUTION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica dónde se ubica un ensamblado.  
  
## Sintaxis  
  
```cpp#  
enum enum_ASSEMBLYLOCRESOLUTION {  
   ALR_NAME      = 0x0,  
   ALR_USERDIR   = 0x1,  
   ALR_SHAREDDIR = 0x2,  
   ALR_REMOTEDIR = 0x4,  
};  
typedef DWORD ASSEMBLYLOCRESOLUTION;  
```  
  
```c#  
public enum enum_ASSEMBLYLOCRESOLUTION {  
   ALR_NAME      = 0x0,  
   ALR_USERDIR   = 0x1,  
   ALR_SHAREDDIR = 0x2,  
   ALR_REMOTEDIR = 0x4,  
};  
```  
  
## Members  
 ALR\_NAME  
 El ensamblado se encuentra en el espacio de nombres actual.  
  
 ALR\_USERDIR  
 El ensamblado se encuentra en un directorio de usuario.  
  
 ALR\_SHAREDDIR  
 El ensamblado se encuentra en el directorio compartido.  
  
 ALR\_REMOTEDIR  
 El ensamblado se encuentra en un directorio remoto.  
  
## Comentarios  
 estos valores son devueltos por los métodos de [ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md) y de [GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md) .  
  
 estos valores se pueden combinar con la operación de `OR` .  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)   
 [GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)