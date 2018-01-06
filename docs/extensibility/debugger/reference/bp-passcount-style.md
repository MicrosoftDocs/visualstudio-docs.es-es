---
title: BP_PASSCOUNT_STYLE | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_PASSCOUNT_STYLE
helpviewer_keywords: BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e272c92bbcc7364c967fc37c1e57b915e6cb64ab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="bppasscountstyle"></a>BP_PASSCOUNT_STYLE
Especifica la condición asociada con el número de paso de punto de interrupción que hace que el punto de interrupción que se active.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
typedef DWORD BP_PASSCOUNT_STYLE;  
```  
  
```csharp  
public enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
```  
  
## <a name="members"></a>Miembros  
 BP_PASSCOUNT_NONE  
 No especifica ningún estilo de número de paso de punto de interrupción.  
  
 BP_PASSCOUNT_EQUAL  
 Establece el estilo de recuento de paso de punto de interrupción en los mismos. El punto de interrupción se desencadena cuando el número de veces que se visita el punto de interrupción es igual que el número de paso.  
  
 BP_PASSCOUNT_EQUAL_OR_GREATER  
 Establece el estilo de número de paso de punto de interrupción en igual o mayor. El punto de interrupción se desencadena cuando el número de veces que se visita el punto de interrupción es igual o mayor que el número de paso.  
  
 BP_PASSCOUNT_MOD  
 Especifica un módulo de recuento de pasos. Por ejemplo, si el número de paso es del tipo `BP_PASSCOUNT_MOD` y el valor de recuento de fase es 4, se activa el punto de interrupción cada vez que el número de llamadas es un múltiplo de 4.  
  
## <a name="remarks"></a>Comentarios  
 Utilizado para la `stylePassCount` miembro de la [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) estructura, que a su vez es un miembro de la [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) y [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) estructuras.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)