---
title: DISASSEMBLY_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d48fcf9dd941194b56e2c794ad7f5673f8e58421
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159317"
---
# <a name="disassembly_flags"></a>DISASSEMBLY_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Especifica las marcas del desensamblado.  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
```csharp  
public enum enum_DISASSEMBLY_FLAGS {   
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
 Indica que esta instrucción está en un documento diferente al anterior.  
  
 DF_DISABLED  
 Indica que esta instrucción no se ejecutará.  
  
 DF_INSTRUCTION_ACTIVE  
 Indica que esta instrucción es una de las instrucciones siguientes que se van a ejecutar (puede haber más de una).  
  
 DF_DATA  
 Indica que esta instrucción es realmente datos (no código).  
  
 DF_HASSOURCE  
 Indica que esta instrucción tiene el origen. Algunas instrucciones, como la generación de perfiles o el código de recolección de elementos no utilizados, no tienen ningún origen correspondiente.  
  
 DF_DOCUMENT_CHECKSUM  
 Indica que `bstrDocumentUrl` el campo contiene datos de suma de comprobación después de la dirección URL del documento. Vea la sección Comentarios de la estructura [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) para saber cómo se almacenan los datos de la suma de comprobación.  
  
## <a name="remarks"></a>Observaciones  
 Se usa como `dwFlags` miembro de la estructura [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) .  
  
 Estas marcas se pueden combinar con una operación bit a bit `OR` .  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
