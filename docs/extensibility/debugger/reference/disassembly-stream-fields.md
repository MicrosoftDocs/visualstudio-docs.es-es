---
title: DISASSEMBLY_STREAM_FIELDS | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 1629e2665d3b02bebba35583561df49d6fdac221
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="disassemblystreamfields"></a>DISASSEMBLY_STREAM_FIELDS
Especifica qué información va a recuperar de un campo de desensamblado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_DISASSEMBLY_STREAM_FIELDS {   
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
  
```csharp  
public enum enum_DISASSEMBLY_STREAM_FIELDS {   
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
  
## <a name="members"></a>Miembros  
 DSF_ADDRESS  
 Inicializar o utilizar el `bstrAddress` campo.  
  
 DSF_ADDRESSOFFSET  
 Inicializar o utilizar el `bstrAddressOffset` campo.  
  
 DSF_CODEBYTES  
 Inicializar o utilizar el `bstrCodeBytes` campo.  
  
 DSF_OPCODE  
 Inicializar o utilizar el `bstrOpCode` campo.  
  
 DSF_OPERANDS  
 Inicializar o utilizar el `bstrOperands` campo.  
  
 DSF_SYMBOL  
 Inicializar o utilizar el `bstrSymbol` campo.  
  
 DSF_CODELOCATIONID  
 Inicializar o utilizar el `uCodeLocationId` campo.  
  
 DSF_POSITION  
 Inicializar o utilizar el `posBeg` y `posEnd` campos.  
  
 DSF_DOCUMENTURL  
 Inicializar o utilizar el `bstrDocumentUrl` campo.  
  
 DSF_BYTEOFFSET  
 Inicializar o utilizar el `dwByteOffset` campo.  
  
 DSF_FLAGS  
 Inicializar o utilizar el `dwFlags` ([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)) campo.  
  
 DSF_OPERANDS_SYMBOLS  
 Incluir nombres de símbolos en el `bstrOperands` campo.  
  
 DSF_ALL  
 Especifica todos los campos de la secuencia de desensamblado.  
  
## <a name="remarks"></a>Comentarios  
 Pasar como un parámetro a la [lectura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) método para indicar qué campos de la [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) estructura deben inicializarse.  
  
 Utilizado para la `dwFields` miembro de la `DisassemblyData` estructura para indicar qué campos se utilizan y válido cuando se devuelve la estructura.  
  
 Estos valores se pueden combinar con un bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [Lectura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)