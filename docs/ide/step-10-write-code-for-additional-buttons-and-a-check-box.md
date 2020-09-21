---
title: Escribir código para botones adicionales y una casilla
description: Aprenda a escribir código para botones adicionales y una casilla en el tutorial Crear un visor de imágenes.
ms.date: 08/30/2019
ms.custom: SEO-VS-2020
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d66f7705821025bd5e30ea0d0c7f2dd57d540e4
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036917"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Paso 10: Escribir código para botones adicionales y una casilla

Ahora, está listo para completar los otros cuatro métodos. Podría copiar y pegar este código, pero si desea aprender lo máximo con este tutorial, escriba el código y utilice IntelliSense.

Este código agrega funcionalidad a los botones que agregó anteriormente. Sin este código, los botones no hacen nada. Los botones utilizan el código de sus eventos <xref:System.Windows.Forms.Control.Click> (y la casilla utiliza el evento <xref:System.Windows.Forms.CheckBox.CheckedChanged>) para realizar diferentes operaciones cuando se activan los controles. Por ejemplo, el evento `clearButton_Click` (o `ClearButton_Click`), que se activa al seleccionar el botón **Borrar la imagen**, borra la imagen actual y establece su propiedad **Image** en **null** (o **nothing**). Cada evento del código incluye comentarios que explican lo que hace el código.

> [!TIP]
> El procedimiento recomendado es comentar siempre el código. Los comentarios son información que leerán otras personas y merece la pena dedicar tiempo a hacer que el código resulte fácil de entender. La aplicación pasa por alto todo lo que hay en una línea de comentario. En C#, para marcar una línea como comentario se escriben dos barras diagonales (//) al principio y en Visual Basic se usa una comilla sencilla (').

## <a name="how-to-write-code-for-additional-buttons-and-a-check-box"></a>Procedimientos para escribir código para botones adicionales y una casilla

Agregue el código siguiente al archivo de código **Form1** (*Form1.cs* o *Form1.vb*).

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]

  [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]

> [!NOTE]
> Es posible que el código no muestre las letras "camelCase".

## <a name="next-steps"></a>Pasos siguientes

* Para ir al siguiente paso del tutorial, vea **[Paso 11: Ejecución de la aplicación y prueba de otras características](../ide/step-11-run-your-program-and-try-other-features.md)** .

* Para volver al paso anterior del tutorial, vea [Paso 9: Revisar, comentar y probar el código](../ide/step-9-review-comment-and-test-your-code.md).

## <a name="see-also"></a>Vea también

* [Tutorial 2: Creación de una prueba matemática cronometrada](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Creación de un juego de formar parejas](tutorial-3-create-a-matching-game.md)
