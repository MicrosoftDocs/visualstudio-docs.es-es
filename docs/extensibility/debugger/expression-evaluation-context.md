---
title: "Contexto de evaluaci&#243;n de expresi&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "evaluación de expresiones, contexto"
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Contexto de evaluaci&#243;n de expresi&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de depuración, **un contexto de evaluación de la expresión**:  
  
-   representa un contexto para la evaluación de la expresión.  Normalmente, un contexto de evaluación corresponde al ámbito léxico dentro del que evaluar variables, parámetros, funciones, y métodos.  Por ejemplo, un contexto de evaluación de la expresión asociada con un marco de pila proporcionará el contexto para las variables locales, los parámetros de método, y los miembros de clase de evaluación \(si procede\).  
  
-   existe cuando un programa ha detenido en un punto de interrupción.  La expresión propia es una estructura de datos que representa una expresión analizada que está lista para enlazar y evaluar dentro del contexto determinado.  
  
     Con más detalle, las expresiones se crean utilizando el método de [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) .  Cuando se evalúa una expresión, genera una cadena imprimible que contiene el nombre y el tipo de variable o argumento y el valor.  Esta cadena se muestra en la ventana inspección o en la ventana Variables locales del IDE.  
  
     Dado `BSTR` y una interfaz de [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) , un motor de depuración se \(DE\) puede crear una interfaz de [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) analizar una expresión.  Proporciona una interfaz de `IDebugExpression2` , el OF puede obtener un valor con la evaluación sincrónica o asincrónica de la expresión.  Este valor, junto con el nombre y el tipo de la variable o el argumento, se envía al IDE para la presentación.  
  
## Vea también  
 [Interfaces de evaluación de expresión](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)