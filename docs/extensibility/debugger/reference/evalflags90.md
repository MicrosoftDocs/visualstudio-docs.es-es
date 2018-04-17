---
title: EVALFLAGS90 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 120bf38afbf05f367757de3a5e453cab8b4311b1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="evalflags90"></a>EVALFLAGS90
Enumera los valores válidos para las marcas que controlan la evaluación de expresiones. Esta enumeración se extiende el [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_EVALFLAGS90  
{  
   // VS 8.0 values  
   EVAL90_RETURNVALUE                 = 0x0002,  
   EVAL90_NOSIDEEFFECTS               = 0x0004,  
   EVAL90_ALLOWBPS                    = 0x0008,  
   EVAL90_ALLOWERRORREPORT            = 0x0010,  
   EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,  
   EVAL90_NOFUNCEVAL                  = 0x0080,  
   EVAL90_NOEVENTS                    = 0x1000,  
   EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,  
   EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,  
  
   // Values added in VS 9.0  
   EVAL90_FORCE_EVALUATION_NOW        = 0x8000  
};  
typedef DWORD EVALFLAGS90;  
```  
  
```csharp  
public enum enum_EVALFLAGS90  
{  
   // VS 8.0 values  
   EVAL90_RETURNVALUE                 = 0x0002,  
   EVAL90_NOSIDEEFFECTS               = 0x0004,  
   EVAL90_ALLOWBPS                    = 0x0008,  
   EVAL90_ALLOWERRORREPORT            = 0x0010,  
   EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,  
   EVAL90_NOFUNCEVAL                  = 0x0080,  
   EVAL90_NOEVENTS                    = 0x1000,  
   EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,  
   EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,  
  
   // Values added in VS 9.0  
   EVAL90_FORCE_EVALUATION_NOW        = 0x8000  
};  
```  
  
#### <a name="parameters"></a>Parámetros  
 EVAL90_RETURNVALUE  
 Especifica que el valor devuelto, si hay alguno, se evaluarán.  
  
 EVAL90_NOSIDEEFFECTS  
 Especifica que no se permiten efectos secundarios.  
  
 EVAL90_ALLOWBPS  
 Especifica detener en los puntos de interrupción.  
  
 EVAL90_ALLOWERRORREPORT  
 Especifica que informe de errores para el host para poder ser admitidos. Se utiliza principalmente para la evaluación de expresión en un script en Internet Explorer.  
  
 EVAL90_FUNCTION_AS_ADDRESS  
 Funciones de fuerza que se debe evaluar como direcciones, en lugar de invocar la función.  
  
 EVAL90_NOFUNCEVAL  
 Impide que función que se va a evaluar. Por ejemplo, considere la `int` símbolo (token) de la expresión `myExpression(int) + 10`. Esta función se puede evaluar correctamente como una dirección, pero no como un valor.  
  
 EVAL90_NOEVENTS  
 Marca para indicar que no se deberían enviar los eventos que se producen durante la evaluación de expresiones para el Administrador de sesión de depuración (SDM) o para el IDE.  
  
 EVAL90_DESIGN_TIME_EXPR_EVAL  
 Permite la evaluación de expresiones en tiempo de diseño.  
  
 EVAL90_ALLOW_IMPLICIT_VARS  
 Permite la creación de variables implícita.  
  
 EVAL90_FORCE_EVALUATION_NOW  
 Evaluación de las fuerzas que se produzca inmediatamente. Esto es útil cuando se atiende una solicitud, por ejemplo, una solicitud de usuario.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Msdbg90.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)