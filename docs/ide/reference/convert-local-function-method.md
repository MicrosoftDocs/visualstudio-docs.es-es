---
title: Convertir una función local en un método
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones para convertir una función local en un método.
ms.custom: SEO-VS-2020
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 3cecafe64f7ead8157a9cb6c80d2f0a245566390
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919717"
---
# <a name="convert-a-local-function-to-a-method"></a>Convertir una función local en un método

Esta refactorización se aplica a lo siguiente:

- C#

**Qué:** Convertir una función local en un método.

**Cuándo:** Tiene una función local que quiere definir fuera del contexto local actual.

**Por qué:** Quiere convertir una función local en un método para poder llamarlo fuera del contexto local. Puede que quiera convertir la función local en un método si esta está creciendo demasiado. Al definir la función en un método independiente, el código es más fácil de leer.

## <a name="convert-local-function-to-method-refactoring"></a>Convertir función local en refactorización de método

1. Coloque el cursor en la función local.

    ![Ejemplo de código de conversión de una función local en un método](media/convert-local-function-to-method.png)

2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.

    ![Ejemplo de corrección del código de conversión de una función local en un método](media/convert-local-function-to-method-codefix.png)

2. Presione ENTRAR para aceptar la refactorización.

    ![Ejemplo de resultados de la conversión de una función local en un método](media/convert-local-function-to-method-result.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
- [Sugerencias para desarrolladores de .NET](../csharp-developer-productivity.md)
