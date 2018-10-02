---
title: PARSEFLAGS | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ccf50c5bd85ae6a69a24da3a3d830009e3297be8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47582194"
---
# <a name="parseflags"></a>PARSEFLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [PARSEFLAGS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/parseflags).  
  
Especifica cómo analizar una expresión.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
typedef DWORD PARSEFLAGS;  
```  
  
```csharp  
public enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
```  
  
## <a name="members"></a>Miembros  
 PARSE_EXPRESSION  
 Indica que la expresión no es una instrucción.  
  
 PARSE_FUNCTION_AS_ADDRESS  
 Indica que es la expresión que se puede analizar (y más adelante se evalúen) como una dirección.  
  
 PARSE_DESIGN_TIME_EXPR_EVAL  
 Indica que la expresión se analiza durante el tiempo de diseño (es decir, cuando un diseñador está abierto).  
  
## <a name="remarks"></a>Comentarios  
 Pasado como parámetro a la [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) y [analizar](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) métodos.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [Analizar](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)

