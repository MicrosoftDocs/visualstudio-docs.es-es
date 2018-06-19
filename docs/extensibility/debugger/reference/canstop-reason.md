---
title: CANSTOP_REASON | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 791132d94526126e8fc611b2becbb8b7545bb578
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109338"
---
# <a name="canstopreason"></a>CANSTOP_REASON
Se utiliza para determinar si un programa puede detener la ejecución tras alcanzar un punto concreto en la ejecución.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
typedef DWORD CANSTOP_REASON;  
```  
  
```csharp  
public enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
```  
  
## <a name="members"></a>Miembros  
 CANSTOP_ENTRYPOINT  
 Especifica el punto de entrada del programa determinado.  
  
 CANSTOP_STEPIN  
 Especifica la ejecución paso a paso en una función.  
  
## <a name="remarks"></a>Comentarios  
 Pasa como un argumento a la [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) método que confirme con el Administrador de sesión de depurar (SDM) si es correcto para detenerse después de alcanzar el punto de entrada del programa o después de la ejecución paso a paso en una función o método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)