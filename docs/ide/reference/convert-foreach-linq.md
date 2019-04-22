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
ms.openlocfilehash: 18c5b01aed925bf458e1c8779a2f41ea1a2d98a4
ms.sourcegitcommit: 7eb85d296146186e7a39a17f628866817858ffb0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59504073"
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
   
### <a name="sample-code"></a>Código de ejemplo

```csharp
using System.Collections.Generic;

public class Class1
{
    public void MyMethod()
    {
        var greetings = new List<string>()
            { "hi", "yo", "hello", "howdy" };

        IEnumerable<string> enumerable()
        {
            foreach (var greet in greetings)
            {
                if (greet.Length < 3)
                {
                    yield return greet;
                }
            }

            yield break;
        }
    }
}
```

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)
- [Sugerencias para desarrolladores de .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
