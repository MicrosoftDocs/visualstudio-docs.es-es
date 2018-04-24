---
title: Sustitución de una variable temporal por su valor en Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 01/26/2018
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
ms.openlocfilehash: 12cce111e3c66018cd10e7e50e9018dc9dbfc4d1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
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

1. A continuación, realice alguno de los siguientes procedimientos:

   - **Teclado**
     - Presione **Ctrl**+**.** para activar el menú **Acciones rápidas y refactorizaciones**.
   - **Mouse**
     - Haga clic en el código y seleccione el menú **Acciones rápidas y refactorizaciones**.

1. Seleccione **Variable temporal en línea** en el menú emergente de la ventana Vista previa.

   La variable se quita y sus usos se reemplazan por el valor de la variable.

   - C#:

    ![Resultado de la inserción (C#)](media/inline-result-cs.png)

   - Visual Basic:

    ![Resultado de la inserción (Visual Basic)](media/inline-result-vb.png)

## <a name="see-also"></a>Vea también

[Refactorización](../refactoring-in-visual-studio.md)