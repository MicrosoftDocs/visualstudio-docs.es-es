---
title: Usar expresión lambda o cuerpo de bloques
ms.date: 02/14/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 5c46506e81e5334efea9060e957269e92e9d49cc
ms.sourcegitcommit: 614d5b99576ea27a41957cd94062dc95cbd29c1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2019
ms.locfileid: "65531911"
---
# <a name="use-expression-body-or-block-body-for-lambda-expressions"></a>Usar cuerpo de expresiones o cuerpo de bloques para expresiones lambda

Esta refactorización se aplica a lo siguiente:

- C#

**Qué:** Permite refactorizar una expresión lambda para usar un cuerpo de expresiones o bloques.

**Cuándo:** Prefiere expresiones lambda para usar un cuerpo de expresiones o bloques.

**Por qué:** Las expresiones lambda se pueden refactorizar a fin de mejorar la legibilidad según las preferencias de usuario.

## <a name="lambda-expression-body-or-block-body-refactoring"></a>Refactorización de cuerpo de expresiones o cuerpo de bloques lambda

1. Coloque el cursor a la derecha de un operador lambda.
2. Presione **Ctrl**+**.** para activar el menú **Acciones rápidas y refactorizaciones**.

  ![Usar expresión lambda o cuerpo de bloques](media/block-body-lambda.png)

3. Seleccione **Use block body for lambda expressions** (Usar cuerpo de bloques para expresiones lambda) o **Use expression body for lambda expressions** (Usar cuerpo de expresiones para expresiones lambda).

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
- [Sugerencias para desarrolladores de .NET](../csharp-developer-productivity.md)