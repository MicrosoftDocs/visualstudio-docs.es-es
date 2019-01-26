---
title: ATTACH_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- ATTACH_REASON
helpviewer_keywords:
- ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d5a7cb8cfbc4efc2ffd90a58c0c0650b677ed8d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966288"
---
# <a name="attachreason"></a>ATTACH_REASON
Especifica la razón para el motor de depuración (DE) para asociar a un nodo de programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
typedef DWORD ATTACH_REASON;  
```  
  
```csharp  
public enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
```  
  
## <a name="members"></a>Miembros  
 ATTACH_REASON_AUTO  
 Adjuntar el proceso está en modo de depuración.  
  
 ATTACH_REASON_LAUNCH  
 Adjuntar porque se ha iniciado el proceso.  
  
 ATTACH_REASON_USER  
 Adjuntar debido a una solicitud de usuario.  
  
## <a name="remarks"></a>Comentarios  
 Estos valores se usan como un parámetro a la [adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md) y [adjuntar](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) métodos.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Asociar](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)