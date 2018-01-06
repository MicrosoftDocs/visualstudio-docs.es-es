---
title: ATTACH_REASON | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ATTACH_REASON
helpviewer_keywords: ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 527e7a445356a46abdd6f2edb0555b7c5c9c7de8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="attachreason"></a>ATTACH_REASON
Especifica la razón para el motor de depuración (Alemania) para asociar a un nodo de programa.  
  
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
 Adjuntar porque el proceso está actualmente en modo de depuración.  
  
 ATTACH_REASON_LAUNCH  
 Adjuntar porque se ha iniciado el proceso.  
  
 ATTACH_REASON_USER  
 Adjuntar debido a una solicitud de usuario.  
  
## <a name="remarks"></a>Comentarios  
 Estos valores se usan como un parámetro a la [adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md) y [adjuntar](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) métodos.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Asociar](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)