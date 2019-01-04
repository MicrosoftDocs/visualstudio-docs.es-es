---
title: MACHINE_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- MACHINE_INFO_FIELDS
helpviewer_keywords:
- MACHINE_INFO_FIELDS enumeration
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 27feb8a47d28569d05afca46d2d773ba855976e2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53830185"
---
# <a name="machineinfofields"></a>MACHINE_INFO_FIELDS
Especifica qué tipo de información que se va a recuperar de una máquina concreta.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
typedef DWORD MACHINE_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
```  
  
## <a name="members"></a>Miembros  
 MCIF_NAME  
 Inicializar o usar el `bstrName` campo en la estructura.  
  
 MCIF_FLAGS  
 Inicializar o usar el `Flags` campo en la estructura.  
  
 MIF_ALL  
 Inicializar o usar todos los campos de la estructura.  
  
## <a name="remarks"></a>Comentarios  
 Estos valores se pasan a la [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) método para indicar qué miembros de la [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) estructura deben inicializarse.  
  
 También se usa en el `Fields` miembro de la `MACHINE_INFO` estructura para indicar qué campos se usan y válido.  
  
 Estas marcas se pueden combinar con un bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)   
 [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)