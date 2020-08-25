---
title: Simplificación de la expresión LINQ
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 04485d6ce67c822fd0620bd63f3557851db6dbb9
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2020
ms.locfileid: "88251362"
---
# <a name="simplify-linq-expression"></a>Simplificación de la expresión LINQ

Esta refactorización se aplica a lo siguiente:

- C#

**Qué:** Refactoriza instancias de `SomeEnumerableType.Where(<LambdaExpression>).Single()` a `SomeEnumerable.Single(<LambdaExpression>)` para `Enumerable.Single()`, así como los siguientes métodos Enumerable: `SingleOrDefault()`, `Last()`, `LastOrDefault()`, `Any()`, `Count()`, `First()` y `FirstOrDefault()`.

**Cuándo:**  Todas las instancias en las que el método llama a `Single()`, `SingleOrDefault()`, etc., no tienen ningún argumento y van precedidos de una expresión `Where()`. La entrada de la expresión `Where()` no se puede construir como un árbol de expresión.

**Por qué:** Al eliminar la llamada innecesaria al objeto enumerable para el método `.Where()`, se mejora el rendimiento y la legibilidad.

## <a name="how-to"></a>Instrucciones

1. Coloque el cursor dentro de la instancia de `SomeEnumerableType.Where(<LambdaExpression>).Single()` en Visual Studio.
2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.
3. Seleccione **Simplify LINQ expression** (Simplificar expresión LINQ).

   ![Conversión de typeof en nameof](media/simplify-linq-expression.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
