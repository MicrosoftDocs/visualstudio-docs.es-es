---
title: "DISASSEMBLY_FLAGS | Microsoft Docs"
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
  - "DISASSEMBLY_FLAGS"
helpviewer_keywords: 
  - "Enumeración DISASSEMBLY_FLAGS"
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# DISASSEMBLY_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica marcadores para desensamblado.  
  
## Sintaxis  
  
```cpp#  
enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
typedef DWORD DISASSEMBLY_FLAGS;  
```  
  
```c#  
public enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
```  
  
## Members  
 DF\_DOCUMENTCHANGE  
 Indica que esta instrucción está en un documento diferente que el anterior.  
  
 DF\_DISABLED  
 Indica que esta instrucción no se ejecutará.  
  
 DF\_INSTRUCTION\_ACTIVE  
 Indica que esta instrucción es una de las siguientes instrucciones de ejecutarse \(puede haber varias\).  
  
 DF\_DATA  
 Indica que esta instrucción es realmente datos \(no código\).  
  
 DF\_HASSOURCE  
 indica que esta instrucción tiene origen.  Algunas instrucciones, como código la generación de perfiles o la recolección de elementos no utilizados, no tienen ningún origen correspondiente.  
  
 DF\_DOCUMENT\_CHECKSUM  
 Indica que el campo de `bstrDocumentUrl` contiene datos de suma de comprobación después de la dirección URL del documento.  Vea la sección comentarios para la estructura de [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) que especifica cómo se almacenan los datos de la suma de comprobación.  
  
## Comentarios  
 Utilizado como miembro de `dwFlags` de la estructura de [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) .  
  
 Estos marcadores se pueden combinar con `OR`bit a bit.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)