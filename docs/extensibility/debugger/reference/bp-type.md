---
title: BP_TYPE | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_TYPE
helpviewer_keywords: BP_TYPE enumeration
ms.assetid: ef07191e-7966-43ab-96fb-1a0b1db3115d
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: eb5f67c34a5e73cd5e1ef049c464a6349c2d5160
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="bptype"></a>BP_TYPE
Especifica si el punto de interrupción está en una ubicación de código, que es una ubicación de datos o que es otro tipo de punto de interrupción.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_BP_TYPE {   
   BPT_NONE    = 0x0000,  
   BPT_CODE    = 0x0001,  
   BPT_DATA    = 0x0002,  
   BPT_SPECIAL = 0x0003  
};  
typedef DWORD BP_TYPE;  
```  
  
```csharp  
public enum enum_BP_TYPE {   
   BPT_NONE    = 0x0000,  
   BPT_CODE    = 0x0001,  
   BPT_DATA    = 0x0002,  
   BPT_SPECIAL = 0x0003  
};  
```  
  
## <a name="members"></a>Miembros  
 BPT_NONE  
 No especifica ningún tipo de punto de interrupción.  
  
 BPT_CODE  
 Especifica un punto de interrupción de código.  
  
 BPT_DATA  
 Especifica un punto de interrupción de datos.  
  
 BPT_SPECIAL  
 Especifica un punto de interrupción que no es un código ni un tipo de datos. Este tipo está en desuso y no debe usarse.  
  
## <a name="remarks"></a>Comentarios  
 Pasar como un parámetro a la [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md) y [GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md) métodos.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)   
 [GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)