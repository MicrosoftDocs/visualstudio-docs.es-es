---
title: BP_COND_STYLE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fbb2674381992bd86f0144af103615f0a3922fcf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153572"
---
# <a name="bp_cond_style"></a>BP_COND_STYLE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Especifica el estilo de condición del punto de interrupción para los puntos de interrupción pendientes y enlazados.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
typedef DWORD BP_COND_STYLE;  
```  
  
```csharp  
public enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
```  
  
## <a name="members"></a>Miembros  
 BP_COND_NONE  
 Activa el punto de interrupción cuando se alcanza la posición del punto de interrupción. No se especificó ninguna condición de punto de interrupción.  
  
 BP_COND_WHEN_TRUE  
 Activa el punto de interrupción solo cuando la expresión condicional asociada al punto de interrupción se evalúa como `true` .  
  
 BP_COND_WHEN_CHANGED  
 Activa el punto de interrupción solo cuando el valor de la expresión condicional asociada al punto de interrupción ha cambiado respecto a su evaluación anterior.  
  
## <a name="remarks"></a>Observaciones  
 Se utiliza para el `styleCondition` miembro de la estructura [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) .  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
