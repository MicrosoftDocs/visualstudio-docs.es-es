---
title: Refactorización de retirada de código no accesible en Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 65dc8a9318c679743030a86c94ad39b3681dc0ad
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896346"
---
# <a name="remove-unreachable-code-refactoring"></a>Refactorización de retirada de código no accesible

Esta refactorización se aplica a lo siguiente:

- C#

**Qué**: Retira código que nunca se ejecutará.

**Cuándo:** El programa no tiene ninguna ruta de acceso a un fragmento de código, lo que convierte a ese fragmento de código en algo innecesario.

**Por qué:** Mejorar la legibilidad y facilidad de mantenimiento mediante la eliminación de código superfluo que nunca se ejecutará.

## <a name="how-to"></a>Procedimiento

1. Coloque el cursor en cualquier lugar del código atenuado que no es accesible:

![Código no accesible atenuado](media/unreachablecode-faded-cs.png)

1. A continuación, realice alguno de los siguientes procedimientos:

   - **Teclado**
      - Presione **Ctrl**+**.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Quitar código inaccesible** en el menú emergente de la ventana Vista previa.
   - **Mouse**
      - Haga clic con el botón derecho en el código, seleccione **Acciones rápidas y refactorizaciones** y elija **Quitar código inaccesible** en el menú emergente de la ventana Vista previa.

1. Cuando esté satisfecho con el cambio, presione **Entrar** o haga clic en la solución en el menú y los cambios se confirmarán.

Ejemplo:

```csharp
// Before
private void Method()
{
    throw new Exception(nameof(Method));
    Console.WriteLine($"Exception for method {nameof(Method)}");
}

// Remove unreachable code

// After
private void Method()
{
    throw new Exception(nameof(Method));
}
```

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)