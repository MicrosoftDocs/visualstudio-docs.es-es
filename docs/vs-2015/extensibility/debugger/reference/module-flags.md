---
title: MODULE_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ae51d604f455b12fd6933a54954b75a97aea4eb7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547473"
---
# <a name="module_flags"></a>MODULE_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Se usa para describir un módulo.  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
```csharp  
public enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
```  
  
## <a name="members"></a>Miembros  
 MODULE_FLAG_NONE  
 No especifica ningún módulo.  
  
 MODULE_FLAG_SYSTEM  
 Especifica un módulo del sistema.  
  
 MODULE_FLAG_SYMBOLS  
 Especifica un módulo de símbolos.  
  
 MODULE_FLAG_64BIT  
 Especifica un módulo de 64 bits.  
  
 MODULE_FLAG_OPTIMIZED  
 Especifica que el módulo se ha optimizado. Este estado se refleja en la ventana **módulos** .  
  
 MODULE_FLAG_UNOPTIMIZED  
 Especifica que el módulo no se ha optimizado. Este estado se refleja en la ventana **módulos** . Este es el estado predeterminado.  
  
## <a name="remarks"></a>Comentarios  
 Se utiliza para el `m_dwModuleFlags` miembro de la estructura [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) .  
  
 Estas marcas se pueden combinar con una operación bit a bit `OR` .  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
