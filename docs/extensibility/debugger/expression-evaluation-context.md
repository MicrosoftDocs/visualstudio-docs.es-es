---
title: Contexto de evaluación de expresiones | Microsoft Docs
description: Obtenga información sobre el contexto de evaluación de expresiones, que representa un contexto para la evaluación de expresiones y existe cuando un programa se ha detenido en un punto de interrupción.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 73eeafb95c7e4d52f69109c5eb7c06eb48bd8d88
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901219"
---
# <a name="expression-evaluation-context"></a>Contexto de evaluación de expresiones
En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la depuración, un contexto **de evaluación de expresiones**:

- Representa un contexto para la evaluación de expresiones. Por lo general, un contexto de evaluación corresponde al ámbito léxico en el que se evalúan variables, parámetros, funciones y métodos. Por ejemplo, un contexto de evaluación de expresión asociado a un marco de pila proporcionará el contexto para evaluar variables locales, parámetros de método y miembros de clase (si procede).

- Existe cuando un programa se ha detenido en un punto de interrupción. La propia expresión es una estructura de datos que representa una expresión analizada que está lista para enlazarse y evaluarse dentro del contexto especificado.

     Con más detalle, las expresiones se crean mediante el [método ParseText.](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) Cuando se evalúa una expresión, genera una cadena imprimible que contiene el nombre y el tipo de variable o argumento y su valor. Esta cadena se muestra en la ventana Inspección o en la ventana Locales del IDE.

     Dado un `BSTR` y una interfaz [IDebugExpressionContext2,](../../extensibility/debugger/reference/idebugexpressioncontext2.md) un motor de depuración (DE) puede crear una [interfaz IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) analizando una expresión. Dada una interfaz, el DE puede obtener un valor mediante la `IDebugExpression2` evaluación de expresiones sincrónicas o asincrónicas. Este valor, junto con el nombre y el tipo de la variable o argumento, se envía al IDE para su presentación.

## <a name="see-also"></a>Consulta también
- [Interfaces de evaluación de expresiones](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Contextos del depurador](../../extensibility/debugger/debugger-contexts.md)
