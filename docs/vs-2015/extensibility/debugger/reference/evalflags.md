---
title: EVALFLAGS | Microsoft Docs
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
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f7e68dc5af0189d7c06f53df1ac1f9976bffe703
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792507"
---
# <a name="evalflags"></a>EVALFLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Especifica las marcas que controlan la evaluación de expresiones.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
};  
typedef DWORD EVALFLAGS;  
```  
  
```csharp  
public enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
}  
```  
  
## <a name="members"></a>Miembros  
 EVAL_RETURNVALUE  
 Especifica que el valor devuelto, si hay alguno, va a evaluar.  
  
 EVAL_NOSIDEEFFECTS  
 Especifica que no se permiten efectos secundarios.  
  
 EVAL_ALLOWBPS  
 Especifica la detención en puntos de interrupción.  
  
 EVAL_ALLOWERRORREPORT  
 Especifica el informe de errores para el host para poder ser admitidos. Se utiliza principalmente para la evaluación de expresión en un script en Internet Explorer.  
  
 EVAL_FUNCTION_AS_ADDRESS  
 Funciones de fuerza se evalúen como direcciones, en lugar de invocar la función.  
  
 EVAL_NOFUNCEVAL  
 Impide a función que se evalúa. Por ejemplo, considere la `int` testigo en la expresión `myExpression(int) + 10`. Esta función se puede evaluar correctamente como una dirección, pero no como un valor.  
  
 EVAL_NOEVENTS  
 Marca para indicar que no se envíen eventos que se producen durante la evaluación de expresión para el Administrador de depuración de la sesión (SDM) o el IDE.  
  
## <a name="remarks"></a>Comentarios  
 Estas marcas se pasan como argumento a la [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) y [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) métodos.  
  
 Estas marcas se pueden combinar con una operación OR bit a bit.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)

