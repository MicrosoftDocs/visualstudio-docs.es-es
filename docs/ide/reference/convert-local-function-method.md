---
title: Convertir función local en método
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 96064b16e53081e0456ed43275acd5edf7ead468
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152959"
---
# <a name="convert-local-function-to-method"></a>Convertir función local en método

Esta refactorización se aplica a lo siguiente:

- C#
- Visual Basic

**Qué:** Convertir una función local en un método

**Cuándo:** Tiene una función local que quiere definir fuera del contexto local actual.

**Por qué:** Quizás quiera convertir una función local en un método para poder llamarlo fuera del contexto local. Quizás quiera convertir en un método si la función local está creciendo demasiado. La definición en un método independiente hace que el código sea más fácil de leer.

## <a name="convert-local-function-to-method-refactoring"></a>Convertir función local en refactorización de método

1. Coloque el cursor en una función local.

    ![Convertir función local en método](media/convert-local-function-to-method.png)

2. Presione **Ctrl**+**.** para activar el menú **Acciones rápidas y refactorizaciones**.

    ![Convertir función local en corrección de código de método](media/convert-local-function-to-method-codefix.png)

2. Presione **ENTRAR** para aceptar la refactorización.

    ![Convertir función local en resultado de método](media/convert-local-function-to-method-result.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
- [Sugerencias para desarrolladores de .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
