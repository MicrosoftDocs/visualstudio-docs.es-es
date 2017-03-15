---
title: "IDebugExpressionEvaluator::Parse | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionEvaluator::Parse"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator::Parse (método)"
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugExpressionEvaluator::Parse
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

este método convierte una cadena de la expresión a una expresión analizada.  
  
## Sintaxis  
  
```cpp#  
HRESULT Parse(   
   LPCOLESTR                upstrExpression,  
   PARSEFLAGS               dwFlags,  
   UINT                     nRadix,  
   BSTR*                    pbstrError,  
   UINT*                    pichError,  
   IDebugParsedExpression** ppParsedExpression  
);  
```  
  
```c#  
int Parse(  
   string                     upstrExpression,   
   enum_PARSEFLAGS            dwFlags,   
   uint                       nRadix,   
   out string                 pbstrError,   
   out uint                   pichError,   
   out IDebugParsedExpression ppParsedExpression  
);  
```  
  
#### Parámetros  
 `upstrExpression`  
 \[in\]  La cadena de expresión que se va a analizar.  
  
 `dwFlags`  
 \[in\]  una colección de constantes de [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) que determinan cómo la expresión debe ser analizada.  
  
 `nRadix`  
 \[in\]  base que se utilizará para interpretar cualquier información numérica.  
  
 `pbstrError`  
 \[out\]  devuelve el error como texto legible.  
  
 `pichError`  
 \[out\]  Devuelve la posición del carácter inicial del error en la cadena de la expresión.  
  
 `ppParsedExpression`  
 \[out\]  devuelve la expresión analizada en un objeto de [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) .  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Este método genera una expresión analizada, no un valor.  Una expresión analizada está lista para evaluar, es decir, convertido en un valor.  
  
## Vea también  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)