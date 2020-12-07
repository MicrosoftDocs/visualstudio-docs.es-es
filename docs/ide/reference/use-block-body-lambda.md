---
title: Usar expresión lambda o cuerpo de bloques
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones para refactorizar una expresión lambda para usar un cuerpo de expresiones o bloques.
ms.custom: SEO-VS-2020
ms.date: 02/14/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 505a76a2300f2e3ddb9c1513ee64c2a17abb10ab
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480179"
---
# <a name="use-expression-body-or-block-body-for-lambda-expressions"></a>Usar cuerpo de expresiones o cuerpo de bloques para expresiones lambda

Esta refactorización se aplica a lo siguiente:

- C#

**Qué:** Permite refactorizar una expresión lambda para usar un cuerpo de expresiones o bloques.

**Cuándo:** Prefiere expresiones lambda para usar un cuerpo de expresiones o bloques.

**Por qué:** Las expresiones lambda se pueden refactorizar a fin de mejorar la legibilidad según las preferencias de usuario.

## <a name="lambda-expression-body-or-block-body-refactoring"></a>Refactorización de cuerpo de expresiones o cuerpo de bloques lambda

1. Coloque el cursor a la derecha de un operador lambda.
2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.

  ![Usar expresión lambda o cuerpo de bloques](media/block-body-lambda.png)

3. Seleccione **Use block body for lambda expressions** (Usar cuerpo de bloques para expresiones lambda) o **Use expression body for lambda expressions** (Usar cuerpo de expresiones para expresiones lambda).

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
- [Sugerencias para desarrolladores de .NET](../csharp-developer-productivity.md)