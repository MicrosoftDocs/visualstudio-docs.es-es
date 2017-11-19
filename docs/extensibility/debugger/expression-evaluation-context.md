---
title: "Contexto de evaluación de expresión | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1ac80a3fcf3a7f75be3f23dd1350da047ccbb393
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="expression-evaluation-context"></a>Contexto de evaluación de expresión
En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuración, un **contexto de evaluación de expresión**:  
  
-   Representa un contexto de evaluación de expresiones. Por lo general, un contexto de evaluación corresponde al ámbito léxico en el que se va a evaluar las variables, parámetros, funciones y métodos. Por ejemplo, un contexto de evaluación de expresión asociado a un marco de pila proporcionará el contexto para evaluar las variables locales, los parámetros de método y los miembros de clase (si procede).  
  
-   Se produce cuando un programa se ha detenido en un punto de interrupción. La expresión es una estructura de datos que representa una expresión analizada que está lista para enlazar y evaluar en el contexto especificado.  
  
     Con más detalle, las expresiones se crean utilizando el [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) método. Cuando se evalúa una expresión, genera una cadena imprimible que contiene el nombre y tipo de variable o argumento y su valor. Esta cadena se muestra en la ventana Inspección o en la ventana variables locales del IDE.  
  
     Dado un `BSTR` y un [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaz, un motor de depuración (Alemania) puede crear un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaz mediante el análisis de una expresión. Dado un `IDebugExpression2` interfaz, el Alemania puede obtener un valor a través de la evaluación de expresiones sincrónico o asincrónico. Este valor, junto con el nombre y tipo de la variable o argumento, se envía el IDE para su presentación.  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de evaluación de expresión](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)