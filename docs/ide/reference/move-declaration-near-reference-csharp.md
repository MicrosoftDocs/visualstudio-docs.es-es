---
title: "Acercamiento de la declaración de variable a la referencia en C# | Microsoft Docs"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: kuhlenh
ms.author: kaseyu
manager: ghogen
dev_langs:
- csharp
ms.workload:
- dotnet
ms.openlocfilehash: f61fbdc8dd24bb07082081557c875e9149c1c398
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/06/2018
---
# <a name="move-declaration-near-reference-in-c"></a>Acercamiento de la declaración a la referencia en C# #

**Qué:** Permite acercar las declaraciones de variable a su uso.

**Cuándo:** Tiene declaraciones de variable que pueden estar en un ámbito más restringido.

**Por qué:**: Puede dejarlo tal cual, pero podría causar problemas de legibilidad u ocultar información. Se trata de una oportunidad de refactorización para mejorar la legibilidad.

**Cómo**:

1. Coloque el cursor en la declaración de variable.

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **Ctrl +.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Mover la declaración cerca de la referencia** en el menú emergente de la ventana Vista previa.
   * **Mouse**
     * Haga clic con el botón derecho en el código, seleccione el menú **Acciones rápidas y refactorizaciones** y elija **Mover la declaración cerca de la referencia** en el menú emergente de la ventana Vista previa.

1. Cuando esté satisfecho con el cambio, presione **Entrar** o haga clic en la solución en el menú y los cambios se confirmarán.

Ejemplo:

```csharp
// Before
int x;
if (condition)
{
    x = 1;
    Console.WriteLine(x);
}

// Move declaration near reference

// After
if (condition)
{
    int x = 1;
    Console.WriteLine(x);
}
```

## <a name="see-also"></a>Vea también

[Refactorización](../refactoring-in-visual-studio.md)  
[Vista previa de cambios](../../ide/preview-changes.md)