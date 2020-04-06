---
title: Contexto de evaluación de expresiones (Expression Evaluation Context) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e939a4fa5f4673e2f701206c96599c54bc0c3b51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738739"
---
# <a name="expression-evaluation-context"></a>Contexto de evaluación de expresiones
En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la depuración, un contexto de evaluación de **expresiones:**

- Representa un contexto para la evaluación de expresiones. Por lo general, un contexto de evaluación corresponde al ámbito léxico dentro del cual se evalúan variables, parámetros, funciones y métodos. Por ejemplo, un contexto de evaluación de expresiones asociado a un marco de pila proporcionará el contexto para evaluar variables locales, parámetros de método y miembros de clase (si corresponde).

- Existe cuando un programa se ha detenido en un punto de interrupción. La propia expresión es una estructura de datos que representa una expresión analizada que está lista para enlazar y evaluar dentro del contexto especificado.

     Con más detalle, las expresiones se crean mediante el [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) método. Cuando se evalúa una expresión, genera una cadena imprimible que contiene el nombre y el tipo de variable o argumento y su valor. Esta cadena se muestra en la ventana Inspección o en la ventana Locales del IDE.

     Dado `BSTR` un y un [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaz, un motor de depuración (DE) puede crear un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaz mediante el análisis de una expresión. Dada `IDebugExpression2` una interfaz, la DE puede obtener un valor a través de la evaluación de expresiones sincrónicas o asincrónicas. Este valor, junto con el nombre y el tipo de la variable o argumento, se envía al IDE para su presentación.

## <a name="see-also"></a>Vea también
- [Interfaces de evaluación de expresiones](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Contextos del depurador](../../extensibility/debugger/debugger-contexts.md)
