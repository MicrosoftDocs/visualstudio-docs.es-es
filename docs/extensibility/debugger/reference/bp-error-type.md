---
title: BP_ERROR_TYPE | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: ab0dc686c4d002733bf8501be042e33c500fb8e3
ms.contentlocale: es-es
ms.lasthandoff: 09/26/2017

---
# <a name="bperrortype"></a>BP_ERROR_TYPE
Especifica el tipo de error de un punto de interrupción.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_BP_ERROR_TYPE {   
   BPET_NONE            = 0x00000000,  
   BPET_TYPE_WARNING    = 0x00000001,  
   BPET_TYPE_ERROR      = 0x00000002,  
   BPET_SEV_HIGH        = 0x0F000000,  
   BPET_SEV_GENERAL     = 0x07000000,  
   BPET_SEV_LOW         = 0x01000000,  
   BPET_TYPE_MASK       = 0x0000ffff,  
   BPET_SEV_MASK        = 0xffff0000,  
   BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,  
   BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,  
   BPET_ALL             = 0xffffffff  
};  
typedef DWORD BP_ERROR_TYPE;  
```  
  
```csharp  
public enum enum_BP_ERROR_TYPE {   
   BPET_NONE            = 0x00000000,  
   BPET_TYPE_WARNING    = 0x00000001,  
   BPET_TYPE_ERROR      = 0x00000002,  
   BPET_SEV_HIGH        = 0x0F000000,  
   BPET_SEV_GENERAL     = 0x07000000,  
   BPET_SEV_LOW         = 0x01000000,  
   BPET_TYPE_MASK       = 0x0000ffff,  
   BPET_SEV_MASK        = 0xffff0000,  
   BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,  
   BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,  
   BPET_ALL             = 0xffffffff  
};  
```  
  
## <a name="members"></a>Miembros  
 BPET_NONE  
 No especifica ningún error de punto de interrupción.  
  
 BPET_TYPE_WARNING  
 Especifica un error de punto de interrupción de advertencia estilo.  
  
 BPET_TYPE_ERROR  
 Especifica un error de punto de interrupción de estilo de error.  
  
 BPET_SEV_HIGH  
 Especifica un error de punto de interrupción de gravedad alta.  
  
 BPET_SEV_GENERAL  
 Especifica un error de punto de interrupción de gravedad Media.  
  
 BPET_SEV_LOW  
 Especifica un error de punto de interrupción de gravedad baja.  
  
 BPET_TYPE_MASK  
 Especifica un error de punto de interrupción de estilo de máscara.  
  
 BPET_SEV_MASK  
 Especifica un error de punto de interrupción de estilo de máscara de gravedad.  
  
 BPET_GENERAL_WARNING  
 Especifica un error de punto de interrupción de estilo de advertencia general.  
  
 BPET_GENERAL_ERROR  
 Especifica un error de punto de interrupción de estilo de error general.  
  
 BPET_ALL  
 Especifica todos los tipos de error de punto de interrupción.  
  
## <a name="remarks"></a>Comentarios  
 Estos valores se pueden combinar con un bit a bit `OR` y se utilizan para la `dwType` miembro de la [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) estructura. Pasar como un parámetro a la [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) método.  
  
 Un tipo de error de punto de interrupción se compone de un tipo y un nivel de gravedad. Esto significa que un tipo de error de punto de interrupción nunca es simplemente un tipo (por ejemplo, `BPET_TYPE_ERROR`,) o un nivel de gravedad (por ejemplo, `BPET_SEV_GENERAL`) por sí mismo. `BPET_GENERAL_WARNING`y `BPET_GENERAL_ERROR` proporcionar valores predefinidos para puntos de interrupción de advertencia y error generales.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
