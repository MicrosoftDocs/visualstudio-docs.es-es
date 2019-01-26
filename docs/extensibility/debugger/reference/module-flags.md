---
title: MODULE_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 32b0e89a69bc39e43d4ff4fbc4e8f4d5816565ad
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54975392"
---
# <a name="moduleflags"></a>MODULE_FLAGS
Se utiliza para describir un módulo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
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
 No especifica que no hay ningún módulo.  
  
 MODULE_FLAG_SYSTEM  
 Especifica un módulo del sistema.  
  
 MODULE_FLAG_SYMBOLS  
 Especifica un módulo de símbolos.  
  
 MODULE_FLAG_64BIT  
 Especifica un módulo de 64 bits.  
  
 MODULE_FLAG_OPTIMIZED  
 Especifica que el módulo se ha optimizado. Este estado se refleja en el **módulos** ventana.  
  
 MODULE_FLAG_UNOPTIMIZED  
 Especifica que el módulo no se ha optimizado. Este estado se refleja en el **módulos** ventana. Este es el estado predeterminado.  
  
## <a name="remarks"></a>Comentarios  
 Utilizado para la `m_dwModuleFlags` miembro de la [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) estructura.  
  
 Estas marcas se pueden combinar con un bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)