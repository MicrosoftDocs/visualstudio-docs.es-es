---
title: Convertir un bucle ForEach en LINQ
description: Convierte cada bucle ForEach que usa un elemento IEnumerable en un formulario de llamada o consulta LINQ (también conocido como un método LINQ).
ms.date: 07/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8ff489e11cc5c61c5e840b4b12d05ba5da46ce41
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466295"
---
# <a name="convert-a-foreach-loop-to-linq"></a>Convertir un bucle ForEach en LINQ

Esta refactorización se aplica a lo siguiente:

- C#

**Qué:** Permite convertir fácilmente el bucle *ForEach* que usa un elemento IEnumerable en un formulario de llamada o consulta LINQ (también conocido como un método LINQ).

**Cuándo:** Tiene un bucle ForEach que usa un elemento IEnumerable y desea que dicho bucle se lea como una consulta LINQ.

**Por qué:** Prefiere usar la sintaxis LINQ en lugar de un bucle ForEach. [LINQ](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq) convierte una consulta en una construcción de lenguaje de primera clase en C#. LINQ puede reducir la cantidad de código de un archivo, facilitar la lectura del código y permitir que distintos orígenes de datos tengan patrones de expresiones de consulta similares.

> [!NOTE]
> La sintaxis LINQ suele ser menos eficaz que un bucle ForEach. Es conveniente conocer todos los inconvenientes para el rendimiento que pueden surgir al usar LINQ para mejorar la legibilidad del código.

## <a name="convert-a-foreach-loop-to-linq-refactoring"></a>Convertir un bucle ForEach en refactorización LINQ

1. Coloque el cursor en la palabra clave `foreach`.

    ![Muestra de ForEach con IEnumerable](media/convert-foreach-to-LINQ.png)

2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.

   ![Muestra de conversión en un menú LINQ](media/convert-foreach-to-LINQ-codefix.png)

3. Seleccione **Convertir a LINQ** o **Convertir a LINQ (formulario de llamada)** .

   ![Muestra de resultado de consulta LINQ](media/convert-foreach-to-LINQ-result.png)

   ![Muestra de resultado de formulario de llamada LINQ](media/convert-foreach-to-LINQ-callform-result.png)

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
- [Ventana para obtener una vista previa de cambios](../../ide/preview-changes.md)
- [Sugerencias para desarrolladores de .NET](../csharp-developer-productivity.md)
