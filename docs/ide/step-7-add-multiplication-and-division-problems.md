---
title: 'Paso 7: Agregar problemas de multiplicación y división'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 64edeb6d6180907e6b1aa07fd5d443e8523c10b1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647465"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>Paso 7: Agregar problemas de multiplicación y división

En la séptima parte de este tutorial, agregará los problemas de multiplicación y división, pero primero piense en cómo realizar ese cambio. Piense en el paso inicial, que requiere almacenar valores.

> [!NOTE]
> Este tema forma parte de una serie de tutoriales sobre conceptos de codificación básicos.
> - Para obtener información general sobre el tutorial, vea [Tutorial 2: Crear una prueba matemática cronometrada](../ide/tutorial-2-create-a-timed-math-quiz.md).
> - Para descargar una versión completa del código, consulte [Ejemplo completo del tutorial de cuestionario de matemáticas](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

## <a name="to-add-multiplication-and-division-problems"></a>Para agregar problemas de multiplicación y división

1. Agregue cuatro variables de entero más al formulario.

     [!code-vb[VbExpressTutorial3Step7#15](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_1.vb)]
     [!code-csharp[VbExpressTutorial3Step7#15](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

2. Tal como hizo antes, modifique el método `StartTheQuiz()` para rellenar los problemas de multiplicación y división con números aleatorios.

     [!code-vb[VbExpressTutorial3Step7#16](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_2.vb)]
     [!code-csharp[VbExpressTutorial3Step7#16](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_2.cs)]

3. Modifique el método `CheckTheAnswer()` para que también compruebe los problemas de multiplicación y división.

     [!code-vb[VbExpressTutorial3Step7#17](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_3.vb)]
     [!code-csharp[VbExpressTutorial3Step7#17](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_3.cs)]

     Dado que no resulta fácil escribir el signo de multiplicación (×) y el signo de división (÷) mediante el teclado, C# y Visual Basic aceptan el asterisco (*) para la multiplicación y la barra diagonal (/) para la división.

4. Cambie la última parte del controlador de evento <xref:System.Windows.Forms.Timer.Tick> del temporizador para que rellene la respuesta correcta cuando se agote el tiempo.

     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]
     [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]

5. Guarde y ejecute el programa.

     Los jugadores deben responder a cuatro problemas para completarla, como se muestra en la ilustración siguiente.

     ![Prueba matemática con cuatro problemas](../ide/media/express_finishedquiz.png)<br/>
***Cuestionario de matemáticas*** *con cuatro problemas*

## <a name="to-continue-or-review"></a>Para continuar o revisar

- Para ir al siguiente paso del tutorial, vea **[Paso 8: Personalizar la prueba](../ide/step-8-customize-the-quiz.md)** .

- Para volver al paso anterior del tutorial, vea [Paso 6: Agregar un problema de resta](../ide/step-6-add-a-subtraction-problem.md).
