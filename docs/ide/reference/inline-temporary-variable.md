---
title: Sustitución de una variable temporal por su valor en Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: fb6fc6888e33b2cc0d210e9cb1e1aababe304f2a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49916769"
---
# <a name="inline-a-temporary-variable-refactoring"></a>Refactorización de inserción de una variable temporal

Esta refactorización se aplica a lo siguiente:

- C#

- Visual Basic

**Qué:** Le permite quitar una variable temporal y reemplazarla por su valor.

**Cuándo:** El uso de la variable temporal dificulta la comprensión del código.

**Quitar:** El hecho de quitar una variable temporal puede facilitar la lectura del código.

## <a name="how-to"></a>Procedimiento

1. Resalte o coloque el cursor de texto dentro de la variable temporal que se va a insertar en línea:

   - C#:

       ![Código resaltado (C#)](media/inline-highlight-cs.png)

   - Visual Basic:

       ![Código resaltado (Visual Basic)](media/inline-highlight-vb.png)

2. A continuación, realice alguno de los siguientes procedimientos:

   - **Teclado**
      - Presione **Ctrl**+**.** para activar el menú **Acciones rápidas y refactorizaciones**.
   - **Mouse**
      - Haga clic en el código y seleccione el menú **Acciones rápidas y refactorizaciones**.

3. Seleccione **Variable temporal en línea** en el menú emergente de la ventana Vista previa.

   La variable se quita y sus usos se reemplazan por el valor de la variable.

   - C#:

      ![Resultado de la inserción (C#)](media/inline-result-cs.png)

   - Visual Basic:

      ![Resultado de la inserción (Visual Basic)](media/inline-result-vb.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)