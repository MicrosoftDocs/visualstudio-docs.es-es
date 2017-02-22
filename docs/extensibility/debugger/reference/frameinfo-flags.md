---
title: "FRAMEINFO_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FRAMEINFO_FLAGS"
helpviewer_keywords: 
  - "Enumeración FRAMEINFO_FLAGS"
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# FRAMEINFO_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica información para recuperar información sobre un objeto del marco de pila.  
  
## Sintaxis  
  
```cpp#  
enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
typedef DWORD FRAMEINFO_FLAGS;  
```  
  
```c#  
public enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
```  
  
## Members  
 FIF\_FUNCNAME  
 Inicializa y usan el campo de `m_bstrFuncName` .  
  
 FIF\_RETURNTYPE  
 Inicializa y usan el campo de `m_bstrReturnType` .  
  
 FIF\_ARGS  
 Inicializa y usan el campo de `m_bstrArgs` .  
  
 FIF\_LANGUAGE  
 Inicializa y usan el campo de `m_bstrLanguage` .  
  
 FIF\_MODULE  
 Inicializa y usan el campo de `m_bstrModule` .  
  
 FIF\_STACKRANGE  
 Inicializa y el uso los campos de `m_addrMin` y de `m_addrMax` \(intervalo de la pila\).  
  
 FIF\_FRAME  
 Inicializa y usan el campo de `m_pFrame` .  
  
 FIF\_DEBUGINFO  
 Inicializa y usan el campo de `m_fHasDebugInfo` .  
  
 FIF\_STALECODE  
 Inicializa y usan el campo de `m_fStaleCode` .  
  
 FIF\_ANNOTATEDFRAME  
 Inicializa y usan el campo de `m_fAnnotatedFrame` .  
  
 FIF\_DEBUG\_MODULEP  
 Inicializa y usan el campo de `m_pModule` .  
  
 FIF\_FUNCNAME\_FORMAT  
 Da formato al nombre de función.  El resultado se devuelve en el campo de `m_bstrFunName` y no se ha completado ningún otro campo.  
  
 FIF\_FUNCNAME\_RETURNTYPE  
 Agrega el tipo de valor devuelto al campo de `m_bstrFuncName` .  
  
 FIF\_FUNCNAME\_ARGS  
 Agrega los argumentos al campo de `m_bstrFuncName` .  
  
 FIF\_FUNCNAME\_LANGUAGE  
 Agrega el idioma al campo de `m_bstrFuncName` .  
  
 FIF\_FUNCNAME\_MODULE  
 Agrega el nombre del módulo al campo de `m_bstrFuncName` .  
  
 FIF\_FUNCNAME\_LINES  
 Agrega el número de líneas al campo de `m_bstrFuncName` .  
  
 FIF\_FUNCNAME\_OFFSET  
 Agrega al campo de `m_bstrFuncName` el desplazamiento de bytes desde el principio de la línea si se especifica `FIF_FUNCNAME_LINES` .  Si `FIF_FUNCNAME_LINES` no se especifica, o si los números de línea no están disponibles, agrega el desplazamiento de bytes desde el principio de la función.  
  
 FIF\_FUNCNAME\_ARGS\_TYPES  
 Agrega el tipo de cada argumento de la función al campo de `m_bstrFuncName` .  
  
 FIF\_FUNCNAME\_ARGS\_NAMES  
 Agrega el nombre de cada argumento de la función al campo de `m_bstrFuncName` .  
  
 FIF\_FUNCNAME\_ARGS\_VALUES  
 Agrega el valor de cada argumento de la función al campo de `m_bstrFuncName` .  
  
 FIF\_FUNCNAME\_ARGS\_ALL  
 Agrega el tipo, el nombre, y el valor de todos los argumentos al campo de `m_bstrFuncName` .  
  
 FIF\_ARGS\_TYPES  
 Recupera y se da formato a los tipos de argumentos.  
  
 FIF\_ARGS\_NAMES  
 Se recuperan y se da formato a los nombres de argumento.  
  
 FIF\_ARGS\_VALUES  
 Se recuperan y se da formato a los valores de argumento.  
  
 FIF\_ARGS\_ALL  
 Recupere y dar formato al tipo, el nombre, y el valor de todos los argumentos.  
  
 FIF\_ARGS\_NOFORMAT  
 Especifica que los argumentos no deben recibir formato \(por ejemplo, no agregue la apertura y los paréntesis de cierre alrededor de la lista de argumentos ni agregue un separador entre los argumentos\).  
  
 FIF\_ARGS\_NO\_FUNC\_EVAL  
 Especifica la evaluación de la función \(propiedad\) no se debe utilizar al recuperar valores de argumento.  
  
 FIF\_FILTER\_NON\_USER\_CODE  
 El motor de depuración es filtrar los cuadros de código de no usuario por lo que no se incluyen.  
  
 FIF\_ARGS\_NO\_TOSTRING  
 No permita la evaluación o formato de función de `ToString()` al devolver argumentos de función.  
  
 FIF\_DESIGN\_TIME\_EXPR\_EVAL  
 La información del marco se debe obtener del dominio de aplicación hospedado en lugar del proceso host.  
  
## Comentarios  
 Estos marcadores se pasan a los métodos de [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) y de [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) para indicar qué campos se deben inicializar en la estructura o las estructuras de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) .  
  
 Estos marcadores también se utilizan para indicar qué campos de la estructura de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) son utilizados y válidos cuando se devuelve la estructura.  estos valores se pueden combinar con `OR`bit a bit.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)