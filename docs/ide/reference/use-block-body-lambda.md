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
ms.openlocfilehash: 1f055925a4da916bf88da802e7a4991b0362b057
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62789437"
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
- [Sugerencias para desarrolladores de .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)