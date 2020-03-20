---
title: 'Paso 4: Agregar el método CheckTheAnswer()'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: def01817fbd42a0da1a0392e00ba9ccff6876470
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579844"
---
# <a name="step-4-add-the-checktheanswer-method"></a>Paso 4: Agregar el método CheckTheAnswer()

En la cuarta parte de este tutorial, escribirá un método, `CheckTheAnswer()`, que determina si las respuestas a los problemas de matemáticas son correctas. Este tema forma parte de una serie de tutoriales sobre conceptos de codificación básicos. Para obtener información general sobre el tutorial, vea [Tutorial 2: Crear una prueba matemática cronometrada](../ide/tutorial-2-create-a-timed-math-quiz.md).

> [!NOTE]
> Este tema forma parte de una serie de tutoriales sobre conceptos de codificación básicos. Para obtener información general sobre el tutorial, vea [Tutorial 2: Crear una prueba matemática cronometrada](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-verify-whether-the-answers-are-correct"></a>Para comprobar si las respuestas son correctas

> [!NOTE]
> Si va a continuar con Visual Basic, utilizará la palabra clave `Function` en lugar de la palabra clave habitual `Sub`, ya que este método devuelve un valor. Realmente es así de sencillo: una subrutina no devuelve ningún valor, una función, sí.

1. Agregue el método `CheckTheAnswer()`.

     Cuando se llama a este método, agrega los valores de addend1 y addend2, y compara el resultado con el valor del control <xref:System.Windows.Forms.NumericUpDown> de suma. Si los valores son iguales, el método devuelve el valor `true`. De lo contrario, el método devuelve el valor `false`. El código debe tener un aspecto parecido al siguiente.

     [!code-vb[VbExpressTutorial3Step4#8](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_1.vb)]
     [!code-csharp[VbExpressTutorial3Step4#8](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Después, puede comprobar la respuesta si actualiza el código del método para que el controlador de eventos <xref:System.Windows.Forms.Timer.Tick> del temporizador llame al nuevo método `CheckTheAnswer()`.

2. Agregue el código siguiente a la instrucción `if else`.

     [!code-vb[VbExpressTutorial3Step4#10](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_2.vb)]
     [!code-csharp[VbExpressTutorial3Step4#10](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_2.cs)]

     Si la respuesta es correcta, `CheckTheAnswer()` devuelve `true`. El controlador de eventos detiene el temporizador, muestra un mensaje de felicitación y hace que el botón **Iniciar** esté disponible de nuevo. De lo contrario, la prueba continúa.

3. Guarde el programa, ejecútelo, inicie una prueba y proporcione una respuesta correcta al problema de suma.

    > [!NOTE]
    > Cuando escriba la respuesta, deberá seleccionar el valor predeterminado antes de empezar a escribir la respuesta o deberá eliminar el cero manualmente. Corregirá este comportamiento más adelante en este tutorial.

     Si proporciona una respuesta correcta, se abre un cuadro de mensaje, el botón **Iniciar** está disponible y el temporizador se detiene.

## <a name="to-continue-or-review"></a>Para continuar o revisar

- Para ir al siguiente paso del tutorial, vea **[Paso 5: Agregar controladores de eventos Enter para los controles NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)** .

- Para volver al paso anterior del tutorial, vea [Paso 3: Agregar un temporizador de cuenta atrás](../ide/step-3-add-a-countdown-timer.md).
