---
title: ATTACH_REASON | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- ATTACH_REASON
helpviewer_keywords:
- ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c66894fe0515b28037bbb2a19715fa09cbf9fa62
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153586"
---
# <a name="attach_reason"></a>ATTACH_REASON
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Especifica el motivo por el que el motor de depuración (DE) se debe adjuntar a un nodo de programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 Asociar porque el proceso está actualmente en modo de depuración.  
  
 ATTACH_REASON_LAUNCH  
 Adjunte porque se ha iniciado el proceso.  
  
 ATTACH_REASON_USER  
 Adjunte debido a una solicitud de usuario.  
  
## <a name="remarks"></a>Comentarios  
 Estos valores se usan como parámetro para los métodos [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) y [Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) .  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Incluir](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Adjuntar](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)
