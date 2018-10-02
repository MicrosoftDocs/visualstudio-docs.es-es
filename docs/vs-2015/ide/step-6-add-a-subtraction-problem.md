---
title: 'Paso 6: Agregar un problema de resta | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59204ef9-24bd-4f81-b85f-e3168e518a3e
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 38b4d8f373d6a3c5069cc2b8f8fe4591ccfa0bcc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47579790"
---
# <a name="step-6-add-a-subtraction-problem"></a>Paso 6: Agregar un problema de resta
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [paso 6: agregar un problema de resta](https://docs.microsoft.com/visualstudio/ide/step-6-add-a-subtraction-problem).  
  
En la sexta parte de este tutorial, agregará un problema de resta y aprenderá a realizar las tareas siguientes:  
  
-   Almacenar los valores de resta.  
  
-   Generar números aleatorios para el problema (y asegurarse de que la respuesta esté comprendida entre 0 y 100).  
  
-   Actualizar el método que comprueba las respuestas para que compruebe también el nuevo problema de resta.  
  
-   Actualizar el controlador eventos Tick del temporizador para que rellene la respuesta correcta cuando se agote el tiempo.  
  
### <a name="to-add-a-subtraction-problem"></a>Para agregar un problema de resta  
  
1.  Agregue al formulario dos variables de entero para el problema de resta (sitúelas entre las variables de entero del problema de suma y el temporizador). El código debe tener este aspecto.  
  
     [!code-csharp[VbExpressTutorial3Step5_6#12](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#12)]
     [!code-vb[VbExpressTutorial3Step5_6#12](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#12)]  
  
     Los nombres de las nuevas variables de entero, **minuend** y **subtrahend**, no son términos de programación. Se trata de los nombres que se utilizan tradicionalmente en aritmética para el número que se resta (sustraendo) y el número del que se resta (minuendo). La diferencia es el minuendo menos el sustraendo. Puede utilizar otros nombres, ya que el programa no requiere nombres específicos para las variables, los controles, los componentes o los métodos. Es necesario seguir ciertas reglas, como que los nombres no comiencen con dígitos, pero normalmente se pueden utilizar nombres como x1, x2, x3 y x4. Sin embargo, los nombres genéricos hacen que el código sea difícil de leer y que el seguimiento de los problemas sea casi imposible. Para que los nombres de variable sean únicos y útiles, se usarán los nombres tradicionales de la multiplicación (multiplicando × multiplicador = producto) y de la división (dividendo ÷ divisor = cociente) más adelante en este tutorial.  
  
     A continuación, modificará el método `StartTheQuiz()` para proporcionar los valores aleatorios del problema de resta.  
  
2.  Agregue el código siguiente después del comentario "Fill in the subtraction problem" (Rellenar el problema de resta).  
  
     [!code-csharp[VbExpressTutorial3Step5_6#13](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#13)]
     [!code-vb[VbExpressTutorial3Step5_6#13](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#13)]  
  
     Para evitar respuestas negativas en el problema de resta, este código utiliza el método `Next()` de la clase `Random` de forma ligeramente diferente a como lo hace el problema de suma. Al asignar dos valores al método `Next()`, este elige un número aleatorio que sea mayor o igual que el primer valor y menor que el segundo. En el código siguiente se elige un número aleatorio del 1 al 100 y se almacena en la variable minuend.  
  
     [!code-csharp[VbExpressTutorial3Step5_6#21](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#21)]
     [!code-vb[VbExpressTutorial3Step5_6#21](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#21)]  
  
     Puede llamar de varias maneras al método `Next()` de la clase `Random`, que denominamos “randomizer” anteriormente en este tutorial. Los métodos a los que se pueden llamar de varias maneras se denominan métodos sobrecargados. Puede utilizar IntelliSense para explorarlos. Fijémonos de nuevo en la información sobre herramientas de la ventana IntelliSense del método `Next()`.  
  
     ![Información sobre herramientas de la ventana IntelliSense](../ide/media/express-overloads.png "Express_Overloads")  
Información sobre herramientas de la ventana IntelliSense  
  
     En la información sobre herramientas se muestra **(+ 2 sobrecargas)**, lo que significa que se puede llamar al método `Next()` de dos formas. Las sobrecargas contienen diferentes números o tipos de argumentos, por lo que funcionan de forma ligeramente distinta una de otra. Por ejemplo, un método puede tomar solamente un argumento entero, mientras que una de las sobrecargas puede tomar un entero y una cadena. Elija la sobrecarga adecuada en función de lo que desee hacer. Cuando agregue código al método `StartTheQuiz()`, aparecerá más información en la ventana de Intellisense en cuanto escriba `randomizer.Next(`. Elija las teclas Flecha arriba y Flecha abajo para recorrer cíclicamente las sobrecargas, tal y como se muestra en la ilustración siguiente.  
  
     ![Sobrecarga del método Next&#40;&#41; en IntelliSense](../ide/media/express-nextoverload.png "Express_NextOverload")  
Sobrecarga del método Next() en IntelliSense  
  
     En este caso, desea elegir la última sobrecarga, ya que puede especificar los valores mínimo y máximo.  
  
3.  Modifique el método `CheckTheAnswer()` para que compruebe si la respuesta de la resta es correcta.  
  
     [!code-csharp[VbExpressTutorial3Step5_6#14](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#14)]
     [!code-vb[VbExpressTutorial3Step5_6#14](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#14)]  
  
     In Visual C#, `&&` es el operador `logical and`. En Visual Basic, el operador equivalente es `AndAlso`. Estos operadores indican "Si la suma de addend1 y addend2 es igual al valor de la suma NumericUpDown, y si el minuendo menos el sustraendo es igual al valor de la diferencia NumericUpDown". El método `CheckTheAnswer()` devuelve `true` solo si las respuestas a los problemas de suma y resta son correctos.  
  
4.  Reemplace la última parte del controlador del evento Tick del temporizador por el código siguiente para que rellene la respuesta correcta cuando se agote el tiempo.  
  
     [!code-csharp[VbExpressTutorial3Step5_6#22](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#22)]
     [!code-vb[VbExpressTutorial3Step5_6#22](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#22)]  
  
5.  Guarde y ejecute el código.  
  
     El programa incluye un problema de resta, como se muestra en la ilustración siguiente.  
  
     ![Prueba matemática con un problema de resta](../ide/media/express-addsubtract.png "Express_AddSubtract")  
Prueba matemática con un problema de resta  
  
### <a name="to-continue-or-review"></a>Para continuar o revisar  
  
-   Para ir al siguiente paso del tutorial, vea [Paso 7: Agregar problemas de multiplicación y división](../ide/step-7-add-multiplication-and-division-problems.md).  
  
-   Para volver al paso anterior del tutorial, vea [Paso 5: Agregar controladores de eventos Enter para los controles NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).



