---
title: Refactorización de retirada de código no accesible
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones para quitar código que nunca se va a ejecutar.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a7ce04b38c13b0994d47974488b90114a63495e6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958120"
---
# <a name="remove-unreachable-code-refactoring"></a>Refactorización de retirada de código no accesible

Esta refactorización se aplica a lo siguiente:

- C#

- Visual Basic

**Qué**: Retira código que nunca se ejecutará.

**Cuándo:** El programa no tiene ninguna ruta de acceso a un fragmento de código, lo que convierte a ese fragmento de código en algo innecesario.

**Por qué:** Mejorar la legibilidad y facilidad de mantenimiento mediante la eliminación de código superfluo que nunca se ejecutará.

## <a name="how-to"></a>Instrucciones

1. Coloque el cursor en cualquier lugar del código atenuado que no es accesible:

![Código no accesible atenuado](media/unreachablecode-faded-cs.png)

1. A continuación, realice alguno de los siguientes procedimientos:

   - **Teclado**
      - Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Quitar código inaccesible** en el menú emergente de la ventana Vista previa.
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
