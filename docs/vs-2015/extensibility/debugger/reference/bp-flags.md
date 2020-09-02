---
title: BP_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_FLAGS
helpviewer_keywords:
- BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7238f41e1971437caaaf3f5aa0c6939c47e27e55
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153519"
---
# <a name="bp_flags"></a>BP_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Proporciona marcas opcionales que se pueden usar para especificar información adicional al establecer un punto de interrupción.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
typedef DWORD BP_FLAGS;  
```  
  
```csharp  
public enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
```  
  
## <a name="members"></a>Miembros  
 BP_FLAG_NONE  
 No especifica ninguna marca de punto de interrupción.  
  
 BP_FLAG_MAP_DOCPOSITION  
 Especifica que el motor DE depuración (DE) debe asignar el punto de interrupción mediante la posición del documento. Esto solo es aplicable a los puntos de interrupción establecidos en archivos de código fuente orientados a scripts como páginas de Active Server (ASP).  
  
 BP_FLAG_DONT_STOP  
 Especifica que el punto de interrupción debe ser procesado por el motor de depuración, pero que el motor de depuración no debe detenerse en última instancia (es decir, no se debe enviar un objeto de evento [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) ). Esta marca está diseñada para usarse principalmente con puntos de seguimiento.  
  
## <a name="remarks"></a>Observaciones  
 Se utiliza para el `dwFlags` miembro de las estructuras [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) y [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .  
  
 Estos valores se pueden combinar con una operación bit a bit `OR` .  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
