---
title: BP_COND_STYLE | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_COND_STYLE
helpviewer_keywords: BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b3d7bd22633985973975cb54d54ab3eb0837e30b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="bpcondstyle"></a>BP_COND_STYLE
Especifica el estilo de condición de punto de interrupción para pendientes y enlaza los puntos de interrupción.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
typedef DWORD BP_COND_STYLE;  
```  
  
```csharp  
public enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
```  
  
## <a name="members"></a>Miembros  
 BP_COND_NONE  
 Se activa el punto de interrupción cuando se alcanza la posición del punto de interrupción. No se especifica ninguna condición de punto de interrupción.  
  
 BP_COND_WHEN_TRUE  
 Se activa el punto de interrupción solo cuando la expresión condicional asociado con el punto de interrupción se evalúa como `true`.  
  
 BP_COND_WHEN_CHANGED  
 Se activa el punto de interrupción sólo cuando el valor de la expresión condicional asociado con el punto de interrupción ha cambiado respecto de su evaluación anterior.  
  
## <a name="remarks"></a>Comentarios  
 Utilizado para la `styleCondition` miembro de la [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) estructura.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)