---
title: Acercamiento de la declaración de variable a la referencia en Visual Studio
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
ms.openlocfilehash: b3a231aafce69bfeeaff7defee6d5f85c7ffc8b2
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896606"
---
# <a name="move-declaration-near-reference-refactoring"></a>Refactorización de acercamiento de la declaración a la referencia

Esta refactorización se aplica a lo siguiente:

- C#

**Qué:** Permite acercar las declaraciones de variable a su uso.

**Cuándo:** Tiene declaraciones de variable que pueden estar en un ámbito más restringido.

**Por qué:**: Puede dejarlo tal cual, pero podría causar problemas de legibilidad u ocultar información. Se trata de una oportunidad de refactorización para mejorar la legibilidad.

## <a name="how-to"></a>Procedimiento

1. Coloque el cursor en la declaración de variable.

1. A continuación, realice alguno de los siguientes procedimientos:

   - **Teclado**
      - Presione **Ctrl**+**.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Mover la declaración cerca de la referencia** en el menú emergente de la ventana Vista previa.
   - **Mouse**
      - Haga clic con el botón derecho en el código, seleccione el menú **Acciones rápidas y refactorizaciones** y elija **Mover la declaración cerca de la referencia** en el menú emergente de la ventana Vista previa.

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

- [Refactorización](../refactoring-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)