---
title: "EVALFLAGS90 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "EVALFLAGS90 (enumeración)"
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# EVALFLAGS90
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Muestra los valores válidos para los marcadores que controlan la evaluación de la expresión.  esta enumeración extiende la enumeración de [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) .  
  
## Sintaxis  
  
```cpp#  
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
  
```c#  
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
  
#### Parámetros  
 EVAL90\_RETURNVALUE  
 Especifica que el valor devuelto, si existe, se evalúa.  
  
 EVAL90\_NOSIDEEFFECTS  
 especifica que los efectos secundarios para no ser permitido.  
  
 EVAL90\_ALLOWBPS  
 Especifica detenerse en los puntos de interrupción.  
  
 EVAL90\_ALLOWERRORREPORT  
 Especifica que informe de errores al host que se permitirá.  Se utiliza principalmente para la evaluación de expresiones en script en Internet Explorer.  
  
 EVAL90\_FUNCTION\_AS\_ADDRESS  
 Convierte las funciones que se evaluarán como direcciones, en lugar de invocar la función.  
  
 EVAL90\_NOFUNCEVAL  
 Impide que la función sea evaluada.  por ejemplo, considere el símbolo de `int` en la expresión `myExpression(int) + 10`.  esta función se puede correctamente evaluar como dirección, pero no como valor.  
  
 EVAL90\_NOEVENTS  
 Marca para indicar que los eventos que se producen durante la evaluación de la expresión no se deberían enviar al administrador \(SDM\) de depuración de la sesión o al IDE.  
  
 EVAL90\_DESIGN\_TIME\_EXPR\_EVAL  
 Permite la evaluación de expresiones en tiempo de diseño.  
  
 EVAL90\_ALLOW\_IMPLICIT\_VARS  
 permite la creación variable implícita.  
  
 EVAL90\_FORCE\_EVALUATION\_NOW  
 Fuerza la evaluación se produzca inmediatamente.  Esto es útil al mantener una solicitud, como una solicitud de usuario.  
  
## Requisitos  
 encabezado: Msdbg90.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)