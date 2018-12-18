---
title: BP_COND_STYLE | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 80b19cec444a009fc62af1b2345ed631ce80ff1c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51784538"
---
# <a name="bpcondstyle"></a>BP_COND_STYLE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Especifica el estilo de condición de punto de interrupción para pendientes y puntos de interrupción enlazados.  
  
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
 Se desencadena el punto de interrupción cuando se alcanza la posición del punto de interrupción. No se especifica ninguna condición de punto de interrupción.  
  
 BP_COND_WHEN_TRUE  
 Se desencadena el punto de interrupción solo cuando la expresión condicional asociado con el punto de interrupción se evalúa como `true`.  
  
 BP_COND_WHEN_CHANGED  
 Se desencadena el punto de interrupción solo cuando el valor de la expresión condicional asociado con el punto de interrupción se ha cambiado respecto a su evaluación anterior.  
  
## <a name="remarks"></a>Comentarios  
 Utilizado para la `styleCondition` miembro de la [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) estructura.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)

