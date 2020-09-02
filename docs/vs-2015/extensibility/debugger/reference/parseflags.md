---
title: PARSEFLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0a9ebe244f3e1c1f3f95508d6df979edee2d4aed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205115"
---
# <a name="parseflags"></a>PARSEFLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Especifica cómo analizar una expresión.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
typedef DWORD PARSEFLAGS;  
```  
  
```csharp  
public enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
```  
  
## <a name="members"></a>Miembros  
 PARSE_EXPRESSION  
 Indica que la expresión no es una instrucción.  
  
 PARSE_FUNCTION_AS_ADDRESS  
 Indica que la expresión se va a analizar (y evaluarse posteriormente) como una dirección.  
  
 PARSE_DESIGN_TIME_EXPR_EVAL  
 Indica que se está analizando la expresión durante el tiempo de diseño (es decir, cuando un diseñador está abierto).  
  
## <a name="remarks"></a>Observaciones  
 Se pasa como parámetro a los métodos [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) y [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) .  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
