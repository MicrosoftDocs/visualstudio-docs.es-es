---
title: BP_PASSCOUNT_STYLE | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3c5a505df625b6ac787f1c13a84e11eddb4d8e7a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47575825"
---
# <a name="bppasscountstyle"></a>BP_PASSCOUNT_STYLE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [BP_PASSCOUNT_STYLE](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/bp-passcount-style).  
  
Especifica la condición asociada con el número de pase de punto de interrupción que hace que el punto de interrupción se activan.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 No especifica que ningún estilo de recuento de pase de punto de interrupción.  
  
 BP_PASSCOUNT_EQUAL  
 Establece el estilo de recuento de pase de punto de interrupción para que sea igual. El punto de interrupción se desencadena cuando el número de veces que se visita el punto de interrupción es igual que el contador de pasos.  
  
 BP_PASSCOUNT_EQUAL_OR_GREATER  
 Establece el estilo de recuento de pase de punto de interrupción en el igual o mayor. El punto de interrupción se desencadena cuando el número de veces que se visita el punto de interrupción es igual o mayor que el recuento de pass.  
  
 BP_PASSCOUNT_MOD  
 Especifica un módulo de recuento de pasos. Por ejemplo, si el contador de pasos es del tipo `BP_PASSCOUNT_MOD` y el valor de recuento de pass es 4, se activa el punto de interrupción cada vez que el recuento de visitas sea un múltiplo de 4.  
  
## <a name="remarks"></a>Comentarios  
 Utilizado para la `stylePassCount` miembro de la [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) estructura que a su vez es miembro de la [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) y [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) estructuras.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)

