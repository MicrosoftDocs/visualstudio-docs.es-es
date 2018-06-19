---
title: DISASSEMBLY_FLAGS | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dd1aa9c73fad40d07be371ad7f9b3108464aeb34
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31101367"
---
# <a name="disassemblyflags"></a>DISASSEMBLY_FLAGS
Especifica las marcas de desensamblado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
typedef DWORD DISASSEMBLY_FLAGS;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
```  
  
## <a name="members"></a>Miembros  
 DF_DOCUMENTCHANGE  
 Indica que esta instrucción es un documento diferente que el anterior.  
  
 DF_DISABLED  
 Indica que esta instrucción no se ejecutarán.  
  
 DF_INSTRUCTION_ACTIVE  
 Indica que esta instrucción es una de las siguientes instrucciones para ejecutarse (puede haber más de uno).  
  
 DF_DATA  
 Indica que esta instrucción es realmente datos (no de código).  
  
 DF_HASSOURCE  
 Indica que esta instrucción tiene código fuente. Algunas instrucciones, por ejemplo, el código de la colección de generación de perfiles o elementos no utilizados, no tengan ningún origen correspondiente.  
  
 DF_DOCUMENT_CHECKSUM  
 Indica que `bstrDocumentUrl` campo contiene datos de suma de comprobación después de la dirección URL del documento. Vea la sección Comentarios para el [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) estructura de cómo se almacenan los datos de suma de comprobación.  
  
## <a name="remarks"></a>Comentarios  
 Usar como el `dwFlags` miembro de la [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) estructura.  
  
 Estas marcas se pueden combinar con un bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)