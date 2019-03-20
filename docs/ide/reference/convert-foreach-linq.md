---
title: Convertir bucle foreach en LINQ
ms.date: 02/20/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: eadad8fdbec990607450b374a32758547194f734
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160279"
---
# <a name="convert-foreach-loop-to-linq"></a>Convertir bucle foreach en LINQ

Esta refactorización se aplica a lo siguiente:

- C#

**Qué:** Permite convertir fácilmente bucles foreach con elementos IEnumerable en formularios de llamada o consulta LINQ (también conocidos como métodos LINQ).

**Cuándo:** Cuando tenga un bucle foreach que usa un elemento IEnumerable que prefiera leer como una consulta LINQ.

**Por qué:** A veces, los usuarios prefieren usar sintaxis LINQ en lugar de un bucle foreach. [LINQ](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq) convierte una consulta en una construcción de lenguaje de primera clase en C#. LINQ puede reducir la cantidad de código de un archivo, facilitar la lectura y permitir que distintos orígenes de datos tengan patrones de expresiones de consulta similares.

> [!NOTE]
> El rendimiento de la sintaxis LINQ suele ser menor que el de los bucles foreach. Es bueno conocer esta desventaja a la hora de mejorar la legibilidad del código con LINQ.

## <a name="convert-foreach-loop-to-linq-refactoring"></a>Convertir bucle foreach en refactorización LINQ

1. Coloque el cursor en la palabra clave `foreach`.

    ![Foreach con IEnumerable](media/convert-foreach-to-LINQ.png)

2. Presione **Ctrl**+**.** para activar el menú **Acciones rápidas y refactorizaciones**.

   ![Convertir en menú LINQ](media/convert-foreach-to-LINQ-codefix.png)

3. Seleccione **Convert to LINQ** (Convertir en LINQ) o **Convert to Linq (call form)** (Convertir en LINQ [formulario de llamada])

   ![Resultado de consulta LINQ](media/convert-foreach-to-LINQ-result.png)
   
   ![Resultado de formulario de llamada LINQ](media/convert-foreach-to-LINQ-callform-result.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)
- [Sugerencias para desarrolladores de .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)