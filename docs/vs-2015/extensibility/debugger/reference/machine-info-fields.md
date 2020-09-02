---
title: MACHINE_INFO_FIELDS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MACHINE_INFO_FIELDS
helpviewer_keywords:
- MACHINE_INFO_FIELDS enumeration
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8cce5300a795922162f2e0b979e553f4235ceacc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147449"
---
# <a name="machine_info_fields"></a>MACHINE_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Especifica qué tipo de información se va a recuperar para un equipo determinado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 Inicializar/usar el `bstrName` campo en la estructura.  
  
 MCIF_FLAGS  
 Inicializar/usar el `Flags` campo en la estructura.  
  
 MIF_ALL  
 Inicialice o utilice todos los campos de la estructura.  
  
## <a name="remarks"></a>Comentarios  
 Estos valores se pasan al método [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) para indicar qué miembros de la estructura de [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) se van a inicializar.  
  
 También se usa en el `Fields` miembro de la `MACHINE_INFO` estructura para indicar qué campos se usan y son válidos.  
  
 Estas marcas se pueden combinar con una operación bit a bit `OR` .  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)   
 [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
