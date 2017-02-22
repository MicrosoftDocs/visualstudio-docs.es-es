---
title: "DISASSEMBLY_STREAM_FIELDS | Microsoft Docs"
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
  - "DISASSEMBLY_STREAM_FIELDS"
helpviewer_keywords: 
  - "Enumeración DISASSEMBLY_STREAM_FIELDS"
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# DISASSEMBLY_STREAM_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica qué información se va a recuperar de un campo de desensamblado.  
  
## Sintaxis  
  
```cpp#  
enum enum_DISASSEMBLY_STREAM_FIELDS {   
   DSF_ADDRESS          = 0x00000001,  
   DSF_ADDRESSOFFSET    = 0x00000002,  
   DSF_CODEBYTES        = 0x00000004,  
   DSF_OPCODE           = 0x00000008,  
   DSF_OPERANDS         = 0x00000010,  
   DSF_SYMBOL           = 0x00000020,  
   DSF_CODELOCATIONID   = 0x00000040,  
   DSF_POSITION         = 0x00000080,  
   DSF_DOCUMENTURL      = 0x00000100,  
   DSF_BYTEOFFSET       = 0x00000200,  
   DSF_FLAGS            = 0x00000400,  
   DSF_OPERANDS_SYMBOLS = 0x00010000,  
   DSF_ALL              = 0x000107ff  
};  
typedef DWORD DISASSEMBLY_STREAM_FIELDS;  
```  
  
```c#  
public enum enum_DISASSEMBLY_STREAM_FIELDS {   
   DSF_ADDRESS          = 0x00000001,  
   DSF_ADDRESSOFFSET    = 0x00000002,  
   DSF_CODEBYTES        = 0x00000004,  
   DSF_OPCODE           = 0x00000008,  
   DSF_OPERANDS         = 0x00000010,  
   DSF_SYMBOL           = 0x00000020,  
   DSF_CODELOCATIONID   = 0x00000040,  
   DSF_POSITION         = 0x00000080,  
   DSF_DOCUMENTURL      = 0x00000100,  
   DSF_BYTEOFFSET       = 0x00000200,  
   DSF_FLAGS            = 0x00000400,  
   DSF_OPERANDS_SYMBOLS = 0x00010000,  
   DSF_ALL              = 0x000107ff  
};  
```  
  
## Members  
 DSF\_ADDRESS  
 Inicializa y usan el campo de `bstrAddress` .  
  
 DSF\_ADDRESSOFFSET  
 Inicializa y usan el campo de `bstrAddressOffset` .  
  
 DSF\_CODEBYTES  
 Inicializa y usan el campo de `bstrCodeBytes` .  
  
 DSF\_OPCODE  
 Inicializa y usan el campo de `bstrOpCode` .  
  
 DSF\_OPERANDS  
 Inicializa y usan el campo de `bstrOperands` .  
  
 DSF\_SYMBOL  
 Inicializa y usan el campo de `bstrSymbol` .  
  
 DSF\_CODELOCATIONID  
 Inicializa y usan el campo de `uCodeLocationId` .  
  
 DSF\_POSITION  
 Inicializa y el uso los campos de `posBeg` y de `posEnd` .  
  
 DSF\_DOCUMENTURL  
 Inicializa y usan el campo de `bstrDocumentUrl` .  
  
 DSF\_BYTEOFFSET  
 Inicializa y usan el campo de `dwByteOffset` .  
  
 DSF\_FLAGS  
 Inicializa y usan el campo de `dwFlags` \([DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)\).  
  
 DSF\_OPERANDS\_SYMBOLS  
 Nombres de símbolos de inclusión en el campo de `bstrOperands` .  
  
 DSF\_ALL  
 Especifica todos los campos de la secuencia de desensamblado.  
  
## Comentarios  
 Pasado como un parámetro al método de [Leer](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) para indicar qué campos de la estructura de [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) se deben inicializar.  
  
 utilizado para el miembro de `dwFields` de la estructura de `DisassemblyData` para indicar qué campos son utilizados y válido cuando se devuelve la estructura.  
  
 estos valores se pueden combinar con `OR`bit a bit.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [Leer](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)