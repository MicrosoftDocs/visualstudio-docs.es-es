---
title: EVALFLAGS | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: EVALFLAGS
helpviewer_keywords: EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 45bef946605818f11d0199600849fd49b5463ab8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="evalflags"></a>EVALFLAGS
Especifica las marcas que controlan la evaluación de expresiones.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_EVALFLAGS {  
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
public enum enum_EVALFLAGS {  
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
 Especifica que el valor devuelto, si hay alguno, se evaluarán.  
  
 EVAL_NOSIDEEFFECTS  
 Especifica que no se permiten efectos secundarios.  
  
 EVAL_ALLOWBPS  
 Especifica detener en los puntos de interrupción.  
  
 EVAL_ALLOWERRORREPORT  
 Especifica los informes de errores para el host para poder ser admitidos. Se utiliza principalmente para la evaluación de expresión en un script en Internet Explorer.  
  
 EVAL_FUNCTION_AS_ADDRESS  
 Funciones de fuerza que se debe evaluar como direcciones, en lugar de invocar la función.  
  
 EVAL_NOFUNCEVAL  
 Impide que función que se va a evaluar. Por ejemplo, considere la `int` símbolo (token) de la expresión `myExpression(int) + 10`. Esta función se puede evaluar correctamente como una dirección, pero no como un valor.  
  
 EVAL_NOEVENTS  
 Marca para indicar que no se deberían enviar los eventos que se producen durante la evaluación de expresiones para el Administrador de sesión de depuración (SDM) o para el IDE.  
  
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