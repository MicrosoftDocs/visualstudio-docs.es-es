---
title: 'Paso 7: Agregar problemas de multiplicación y división | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a558372c69aaf5aeb76685cae3eae4f30a6b9737
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54795273"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>Paso 7: Agregar problemas de multiplicación y división
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En la séptima parte de este tutorial, agregará los problemas de multiplicación y división, pero primero piense en cómo realizar ese cambio. Piense en el paso inicial, que requiere almacenar valores.  
  
### <a name="to-add-multiplication-and-division-problems"></a>Para agregar problemas de multiplicación y división  
  
1.  Agregue cuatro variables de entero más al formulario.  
  
     [!code-csharp[VbExpressTutorial3Step7#15](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#15)]
     [!code-vb[VbExpressTutorial3Step7#15](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#15)]  
  
2.  Tal como hizo antes, modifique el método `StartTheQuiz()` para rellenar los problemas de multiplicación y división con números aleatorios.  
  
     [!code-csharp[VbExpressTutorial3Step7#16](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#16)]
     [!code-vb[VbExpressTutorial3Step7#16](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#16)]  
  
3.  Modifique el método `CheckTheAnswer()` para que también compruebe los problemas de multiplicación y división.  
  
     [!code-csharp[VbExpressTutorial3Step7#17](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#17)]
     [!code-vb[VbExpressTutorial3Step7#17](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#17)]  
  
     Dado que no resulta fácil escribir el signo de multiplicación (×) y el signo de división (÷) mediante el teclado, Visual C# y Visual Basic aceptan el asterisco (*) para la multiplicación y la barra diagonal (/) para la división.  
  
4.  Cambie la última parte del controlador de evento Tick del temporizador para que rellene la respuesta correcta cuando se agote el tiempo.  
  
     [!code-csharp[VbExpressTutorial3Step7#23](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#23)]
     [!code-vb[VbExpressTutorial3Step7#23](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#23)]  
  
5.  Guarde y ejecute el programa.  
  
     Los jugadores deben responder a cuatro problemas para completarla, como se muestra en la ilustración siguiente.  
  
     ![Prueba matemática con cuatro problemas](../ide/media/express-finishedquiz.png "Express_FinishedQuiz")  
Prueba matemática con cuatro problemas  
  
### <a name="to-continue-or-review"></a>Para continuar o revisar  
  
-   Para ir al siguiente paso del tutorial, vea [Paso 8: Personalizar la prueba](../ide/step-8-customize-the-quiz.md).  
  
-   Para volver al paso anterior del tutorial, vea [Paso 6: Agregar un problema de resta](../ide/step-6-add-a-subtraction-problem.md).
