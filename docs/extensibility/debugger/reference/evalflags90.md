---
title: EVALFLAGS90 | Microsoft Docs
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
ms.openlocfilehash: 43c8c7dcba7ea1125c031f0cc64a902d88f67017
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49849435"
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
 Especifica que el valor devuelto, si hay alguno, va a evaluar.  
  
 EVAL90_NOSIDEEFFECTS  
 Especifica que no se permiten efectos secundarios.  
  
 EVAL90_ALLOWBPS  
 Especifica la detención en puntos de interrupción.  
  
 EVAL90_ALLOWERRORREPORT  
 Especifica que informe de errores para el host para poder ser admitidos. Se utiliza principalmente para la evaluación de expresión en un script en Internet Explorer.  
  
 EVAL90_FUNCTION_AS_ADDRESS  
 Funciones de fuerza se evalúen como direcciones, en lugar de invocar la función.  
  
 EVAL90_NOFUNCEVAL  
 Impide a función que se evalúa. Por ejemplo, considere la `int` testigo en la expresión `myExpression(int) + 10`. Esta función se puede evaluar correctamente como una dirección, pero no como un valor.  
  
 EVAL90_NOEVENTS  
 Marca para indicar que no se envíen eventos que se producen durante la evaluación de expresión para el Administrador de depuración de la sesión (SDM) o el IDE.  
  
 EVAL90_DESIGN_TIME_EXPR_EVAL  
 Permite la evaluación de expresiones en tiempo de diseño.  
  
 EVAL90_ALLOW_IMPLICIT_VARS  
 Permite la creación implícita de variables.  
  
 EVAL90_FORCE_EVALUATION_NOW  
 Evaluación de las fuerzas que se produzca inmediatamente. Esto es útil cuando se atiende una solicitud, por ejemplo, una solicitud de usuario.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Msdbg90.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)