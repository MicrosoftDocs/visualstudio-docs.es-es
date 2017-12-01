---
title: "Quitar código inalcanzable - refactorización (C#) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
author: kuhlenh
ms.author: kaseyu
manager: ghogen
dev_langs: csharp
ms.openlocfilehash: d4dfc63000fe6f66135d452b9a64e14dc05101d9
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/29/2017
---
# <a name="remove-unreachable-code-in-c"></a>Quite el código inalcanzable en C# #
**¿Qué:** quita el código que nunca se ejecutará.

**Cuándo:** el programa no tiene ninguna ruta de acceso a un fragmento de código, realizar ese fragmento de código innecesario.

**Por este motivo:** mejorar la legibilidad y facilidad de mantenimiento mediante la eliminación de código que es superflua y nunca se ejecutará.

**Cómo:**

1. Coloque el cursor en cualquier lugar en el código de desvanecimiento espera que no es accesible:

![Atenuado código inalcanzable](media/unreachablecode_faded.png)  

1. A continuación, realice una de las siguientes acciones:
   * **Teclado**
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione **quite código inalcanzable** desde la ventana emergente de ventana de vista previa.
   * **Mouse**
     * Haga clic en el código, seleccione la **acciones rápidas y refactorizaciones** menú y seleccione **quite código inalcanzable** desde la ventana emergente de ventana de vista previa.

1. Cuando esté satisfecho con el cambio, presione **ENTRAR** o haga clic en la solución en el menú y los cambios se confirmarán.

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
[Refactorización (C#)](../refactoring-csharp.md)  
[Vista previa de cambios](../../ide/preview-changes.md)