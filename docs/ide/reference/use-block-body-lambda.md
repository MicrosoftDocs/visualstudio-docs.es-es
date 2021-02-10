---
title: Usar expresión lambda o cuerpo de bloques
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones para refactorizar una expresión lambda para usar un cuerpo de expresiones o bloques.
ms.custom: SEO-VS-2020
ms.date: 02/14/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: bc3b80ad625c58fbe9127978ebc23fd8c764f4d3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889907"
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