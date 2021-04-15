---
title: 'Paso 7: Agregar problemas de multiplicación y división'
description: Aprenda a agregar problemas de multiplicación y división.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6443d80b2dba347691dd6721da19518dc86c71bf
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2021
ms.locfileid: "107297033"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>Paso 7: Agregar problemas de multiplicación y división

En la séptima parte de este tutorial, agregará los problemas de multiplicación y división, pero primero piense en cómo realizar ese cambio. Piense en el paso inicial, que requiere almacenar valores.

> [!NOTE]
> Este tema forma parte de una serie de tutoriales sobre conceptos de codificación básicos. Para obtener información general sobre el tutorial, vea [Tutorial 2: Crear una prueba matemática cronometrada](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-add-multiplication-and-division-problems"></a>Para agregar problemas de multiplicación y división

1. Agregue cuatro variables de entero más al formulario.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb" id="Snippet15":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs" id="Snippet15":::

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

2. Tal como hizo antes, modifique el método `StartTheQuiz()` para rellenar los problemas de multiplicación y división con números aleatorios.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb" id="Snippet16":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs" id="Snippet16":::

3. Modifique el método `CheckTheAnswer()` para que también compruebe los problemas de multiplicación y división.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb" id="Snippet17":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs" id="Snippet17":::

     Dado que no resulta fácil escribir el signo de multiplicación (×) y el signo de división (÷) mediante el teclado, C# y Visual Basic aceptan el asterisco (*) para la multiplicación y la barra diagonal (/) para la división.

4. Cambie la última parte del controlador de evento <xref:System.Windows.Forms.Timer.Tick> del temporizador para que rellene la respuesta correcta cuando se agote el tiempo.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb" id="Snippet23":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs" id="Snippet23":::

5. Guarde y ejecute el programa.

     Los jugadores deben responder a cuatro problemas para completarla, como se muestra en la ilustración siguiente.

     ![Prueba matemática con cuatro problemas](../ide/media/express_finishedquiz.png)<br/>
***Prueba matemática** _ _con cuatro problemas*

## <a name="to-continue-or-review"></a>Para continuar o revisar

- Para ir al siguiente paso del tutorial, vea **[Paso 8: Personalizar la prueba](../ide/step-8-customize-the-quiz.md)** .

- Para volver al paso anterior del tutorial, vea [Paso 6: Agregar un problema de resta](../ide/step-6-add-a-subtraction-problem.md).
