---
title: 'Paso 3: Agregar un temporizador de cuenta atrás'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 62670a2b-efdc-45c6-9646-9b17eeb33dcb
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d1f8fdd4bebba62d43c2868fa42d87a8c0fada0b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="step-3-add-a-countdown-timer"></a>Paso 3: Agregar un temporizador de cuenta atrás
En la tercera parte de este tutorial, agregará un temporizador de cuenta atrás para el seguimiento del número de segundos que quedan para que el jugador finalice.  

> [!NOTE]
>  Este tema forma parte de una serie de tutoriales sobre conceptos de codificación básicos. Para obtener información general sobre el tutorial, vea [Tutorial 2: Crear una prueba matemática cronometrada](../ide/tutorial-2-create-a-timed-math-quiz.md).  

### <a name="to-add-a-countdown-timer"></a>Para agregar un temporizador de cuenta atrás  

1.  Agregue una variable de entero denominada **timeLeft**, como hizo en el procedimiento anterior. El código debe tener un aspecto parecido al siguiente.  

     [!code-vb[VbExpressTutorial3Step3#5](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_1.vb)]
     [!code-csharp[VbExpressTutorial3Step3#5](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_1.cs)]  

     Ahora necesita un método que cuente realmente los segundos, como un temporizador, y que genere un evento después del tiempo especificado.  

2.  En la ventana de diseño, mueva un control `Timer` de la categoría **Componentes** del cuadro de herramientas al formulario.  

     El control aparece en el área gris de la parte inferior de la ventana de diseño.  

3.  En el formulario, pulse el icono **timer1** que acaba de agregar y establezca su propiedad **Interval** en **1000**.  

     Dado que el valor de intervalo está en milisegundos, el valor 1000 hace que el evento Tick se genere cada segundo.  

4.  En el formulario, haga doble clic en el control Timer o selecciónelo y elija la tecla Entrar.  

     Aparece un editor de código en el que se muestra el método del controlador de eventos Tick que acaba de agregar.  

5.  Agregue las siguientes instrucciones al nuevo método de control de eventos.  

     [!code-vb[VbExpressTutorial3Step3#6](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_2.vb)]
     [!code-csharp[VbExpressTutorial3Step3#6](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_2.cs)]  

     En función de lo que haya agregado, el temporizador comprobará cada segundo si se ha agotado el tiempo, determinando si la variable de entero **timeLeft** es mayor que 0. Si es así, todavía queda tiempo. En primer lugar, el temporizador resta 1 a timeLeft y, después, actualiza la propiedad **Text** del control `timeLabel` para mostrar al jugador cuántos segundos quedan.  

     Si no queda tiempo, el temporizador se detiene y cambia el texto del control `timeLabel` para que muestre que **se ha agotado el tiempo**. Un cuadro de mensaje anuncia que la prueba ha finalizado y revela la respuesta; en este caso, la suma de addend1 y addend2. La propiedad **Enabled** del control `startButton` se establece en `true` para que el jugador pueda iniciar otra prueba.  

     Hemos agregado una instrucción `if else`, que es la manera de indicar a los programas que tomen decisiones. Una instrucción `if else` tiene el siguiente aspecto.  

    > [!NOTE]
    >  El ejemplo siguiente tiene solo fines ilustrativos. No lo agregue al proyecto.  

    ```vb  
    If (something that your program will check) Then  
        ' One or more statements that will run  
        ' if what the program checked is true.   
    Else  
        ' One or more statements that will run  
        ' if what the program checked is false.  
    End If  
    ```  

    ```csharp  
    if (something that your program will check)  
    {  
        // One or more statements that will run  
        // if what the program checked is true.   
    }  
    else  
    {  
        // One or more statements that will run  
        // if what the program checked is false.  
    }  
    ```  

     Vamos a fijarnos con más atención en la instrucción que hemos agregado en el bloque `else` para mostrar la respuesta al problema de suma.  

     [!code-vb[VbExpressTutorial3Step3#24](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_3.vb)]
     [!code-csharp[VbExpressTutorial3Step3#24](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_3.cs)]  

     La instrucción `addend1 + addend2` suma los valores de las dos variables. La primera parte (`sum.Value`) usa la propiedad **Value** del control `NumericUpDown` de la suma para mostrar la respuesta correcta. Utilizará la misma propiedad más adelante para comprobar las respuestas de la prueba.  

     Los usuarios pueden escribir los números con más facilidad si se usa un control `NumericUpDown`. Este es el motivo por el que se usa este control para las respuestas a los problemas de matemáticas. Todas las respuestas posibles son números enteros comprendidos entre 0 y 100. Al dejar los valores predeterminados de las propiedades **Minimum**, **Maximum** y **DecimalPlaces**, se asegura de que los jugadores no puedan escribir decimales, números negativos o números que sean demasiado altos. (Si quiere permitir que los jugadores escriban 3,141 pero no 3,1415, puede establecer la propiedad **DecimalPlaces** en 3).  

6.  Agregue tres líneas al final de método `StartTheQuiz()`, de modo que el código tenga este aspecto.  

     [!code-vb[VbExpressTutorial3Step3#7](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_4.vb)]
     [!code-csharp[VbExpressTutorial3Step3#7](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_4.cs)]  

     Ahora, al empezar la prueba, la variable **timeLeft** se establece en 30 y la propiedad **Text** del control `timeLabel` se establece en 30 segundos. Después, el método `Start()` del control `Timer` inicia la cuenta atrás. (La prueba no comprueba la respuesta todavía, esto viene después).  

7.  Guarde el programa, ejecútelo y, después, pulse el botón **Iniciar** en el formulario.  

     El temporizador iniciará la cuenta atrás. Cuando se agota el tiempo, la prueba finaliza y se muestra la respuesta. En la ilustración siguiente se muestra la prueba en curso.  

     ![Prueba matemática en curso](../ide/media/express_addcountdown.png "Express_AddCountdown")  
Prueba matemática en curso  

### <a name="to-continue-or-review"></a>Para continuar o revisar  

-   Para ir al siguiente paso del tutorial, vea [Paso 4: Agregar el método CheckTheAnswer()](../ide/step-4-add-the-checktheanswer-parens-method.md).  

-   Para volver al paso anterior del tutorial, vea [Paso 2: Crear un problema de suma aleatoria](../ide/step-2-create-a-random-addition-problem.md).
