---
title: Convertir una función local en un método
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3572682fe68d9b0b1bc4adee537de5cd056a8906
ms.sourcegitcommit: 9a3972eb85de5443ac2bc03964c5a251c39b2921
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/26/2019
ms.locfileid: "71301691"
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
