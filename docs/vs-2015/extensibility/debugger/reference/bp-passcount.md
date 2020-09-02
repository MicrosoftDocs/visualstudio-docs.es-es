---
title: BP_PASSCOUNT | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT
helpviewer_keywords:
- BP_PASSCOUNT structure
ms.assetid: 791ac175-b897-4c70-873e-240da7e0ac89
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b99cbd777755a9a48869299b5cea523ecacbb4a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153377"
---
# <a name="bp_passcount"></a>BP_PASSCOUNT
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Describe el recuento y las condiciones en las que se desencadena un punto de interrupción condicional.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
typedef struct _BP_PASSCOUNT {   
   DWORD              dwPassCount;  
   BP_PASSCOUNT_STYLE stylePassCount;  
} BP_PASSCOUNT;  
```  
  
```csharp  
public struct BP_PASSCOUNT {   
   public uint dwPassCount;  
   public uint stylePassCount;  
};  
```  
  
## <a name="members"></a>Miembros  
 `dwPassCount`  
 Número de veces que se va a pasar el punto de interrupción antes de activarlo.  
  
 `stylePassCount`  
 Un valor de la enumeración [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md) que especifica el estilo del recuento de pasos de punto de interrupción.  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura es un miembro de la estructura [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) .  
  
 Esta estructura también se pasa como parámetro a los métodos[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md) y[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md) .  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)   
 [SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)   
 [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)
