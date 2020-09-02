---
title: FRAMEINFO_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e5a930e81ff1105ba93ce3c3cff10ee8bff2f7e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538439"
---
# <a name="frameinfo_flags"></a>FRAMEINFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Especifica la información que se va a recuperar sobre un objeto de marco de pila.  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
```csharp  
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
  
## <a name="members"></a>Miembros  
 FIF_FUNCNAME  
 Inicializar/usar el `m_bstrFuncName` campo.  
  
 FIF_RETURNTYPE  
 Inicializar/usar el `m_bstrReturnType` campo.  
  
 FIF_ARGS  
 Inicializar/usar el `m_bstrArgs` campo.  
  
 FIF_LANGUAGE  
 Inicializar/usar el `m_bstrLanguage` campo.  
  
 FIF_MODULE  
 Inicializar/usar el `m_bstrModule` campo.  
  
 FIF_STACKRANGE  
 Inicialice o use los `m_addrMin` `m_addrMax` campos y (intervalo de pila).  
  
 FIF_FRAME  
 Inicializar/usar el `m_pFrame` campo.  
  
 FIF_DEBUGINFO  
 Inicializar/usar el `m_fHasDebugInfo` campo.  
  
 FIF_STALECODE  
 Inicializar/usar el `m_fStaleCode` campo.  
  
 FIF_ANNOTATEDFRAME  
 Inicializar/usar el `m_fAnnotatedFrame` campo.  
  
 FIF_DEBUG_MODULEP  
 Inicializar/usar el `m_pModule` campo.  
  
 FIF_FUNCNAME_FORMAT  
 Da formato al nombre de la función. El resultado se devuelve en el `m_bstrFunName` campo y no se rellena ningún otro campo.  
  
 FIF_FUNCNAME_RETURNTYPE  
 Agrega el tipo de valor devuelto al `m_bstrFuncName` campo.  
  
 FIF_FUNCNAME_ARGS  
 Agrega los argumentos al `m_bstrFuncName` campo.  
  
 FIF_FUNCNAME_LANGUAGE  
 Agrega el idioma al `m_bstrFuncName` campo.  
  
 FIF_FUNCNAME_MODULE  
 Agrega el nombre del módulo al `m_bstrFuncName` campo.  
  
 FIF_FUNCNAME_LINES  
 Agrega el número de líneas al `m_bstrFuncName` campo.  
  
 FIF_FUNCNAME_OFFSET  
 Agrega al `m_bstrFuncName` campo el desplazamiento en bytes desde el inicio de la línea si `FIF_FUNCNAME_LINES` se especifica. Si `FIF_FUNCNAME_LINES` no se especifica, o si los números de línea no están disponibles, agrega el desplazamiento en bytes desde el inicio de la función.  
  
 FIF_FUNCNAME_ARGS_TYPES  
 Agrega el tipo de cada argumento de función al `m_bstrFuncName` campo.  
  
 FIF_FUNCNAME_ARGS_NAMES  
 Agrega el nombre de cada argumento de función al `m_bstrFuncName` campo.  
  
 FIF_FUNCNAME_ARGS_VALUES  
 Agrega el valor de cada argumento de función al `m_bstrFuncName` campo.  
  
 FIF_FUNCNAME_ARGS_ALL  
 Agrega el tipo, el nombre y el valor de todos los argumentos al `m_bstrFuncName` campo.  
  
 FIF_ARGS_TYPES  
 Los tipos de argumento se recuperan y se les da formato.  
  
 FIF_ARGS_NAMES  
 Los nombres de los argumentos se recuperan y se les da formato.  
  
 FIF_ARGS_VALUES  
 Los valores de argumento se recuperan y se les da formato.  
  
 FIF_ARGS_ALL  
 Recupere y formatee el tipo, el nombre y el valor de todos los argumentos.  
  
 FIF_ARGS_NOFORMAT  
 Especifica que no se debe dar formato a los argumentos (por ejemplo, no agregue paréntesis de apertura y cierre alrededor de la lista de argumentos ni agregue un separador entre los argumentos).  
  
 FIF_ARGS_NO_FUNC_EVAL  
 Especifica que no se debe usar la evaluación de función (propiedad) al recuperar los valores de argumento.  
  
 FIF_FILTER_NON_USER_CODE  
 El motor de depuración consiste en filtrar marcos de código que no son de usuario para que no se incluyan.  
  
 FIF_ARGS_NO_TOSTRING  
 No permita la `ToString()` evaluación o el formato de funciones al devolver argumentos de función.  
  
 FIF_DESIGN_TIME_EXPR_EVAL  
 La información del marco debe obtenerse del dominio de aplicación hospedado en lugar del proceso de hospedaje.  
  
## <a name="remarks"></a>Comentarios  
 Estas marcas se pasan a los métodos [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) y [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) para indicar qué campos se van a inicializar en la estructura o estructuras de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) .  
  
 Estas marcas también se usan para indicar qué campos de la estructura [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) se usan y son válidos cuando se devuelve la estructura. Estos valores se pueden combinar con una operación bit a bit `OR` .  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
