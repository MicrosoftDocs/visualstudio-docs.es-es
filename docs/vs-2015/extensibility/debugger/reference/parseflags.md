---
title: PARSEFLAGS | Documentos de Microsoft
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
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 68eaa04da057d514a833b86efd1fd08ea807fe6e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49187564"
---
# <a name="parseflags"></a>PARSEFLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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

