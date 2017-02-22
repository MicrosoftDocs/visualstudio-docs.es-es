---
title: "Paso 4: Agregar el m&#233;todo CheckTheAnswer() | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Paso 4: Agregar el m&#233;todo CheckTheAnswer()
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En la cuarta parte de este tutorial, escribirá un método, `CheckTheAnswer()`, que determina si las respuestas a los problemas de matemáticas son correctas.  Este tema forma parte de una serie de tutoriales sobre conceptos de codificación básicos.  Para obtener información general sobre el tutorial, vea [Tutorial 2: Crear una prueba matemática cronometrada](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
> [!NOTE]
>  Si va a continuar con Visual Basic, utilizará la palabra clave `Function` en lugar de la palabra clave habitual `Sub`, ya que este método devuelve un valor.  Realmente es así de sencillo: una subrutina no devuelve ningún valor, una función, sí.  
  
### Para comprobar si las respuestas son correctas  
  
1.  Agregue el método `CheckTheAnswer()`.  
  
     Cuando se llama a este método, agrega los valores de addend1 y addend2 y compara el resultado con el valor del control `NumericUpDown` de suma.  Si los valores son iguales, el método devuelve el valor `true`.  De lo contrario, el método devuelve el valor `false`.  El código debe tener un aspecto parecido al siguiente.  
  
     [!code-vb[VbExpressTutorial3Step4#8](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_1.vb)]
     [!code-cs[VbExpressTutorial3Step4#8](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_1.cs)]  
  
     A continuación, puede comprobar la respuesta actualizando el código del método para que el controlador de eventos Tick del temporizador llame al nuevo método `CheckTheAnswer()`.  
  
2.  Agregue el código siguiente a la instrucción `if else`.  
  
     [!code-vb[VbExpressTutorial3Step4#10](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_2.vb)]
     [!code-cs[VbExpressTutorial3Step4#10](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_2.cs)]  
  
     Si la respuesta es correcta, `CheckTheAnswer()` devuelve `true`.  El controlador de eventos detiene el temporizador, muestra un mensaje de felicitación y hace que el botón **Iniciar** esté disponible de nuevo.  De lo contrario, la prueba continúa.  
  
3.  Guarde el programa, ejecútelo, inicie una prueba y proporcione una respuesta correcta al problema de suma.  
  
    > [!NOTE]
    >  Cuando escriba la respuesta, deberá seleccionar el valor predeterminado antes de empezar a escribir la respuesta o deberá eliminar el cero manualmente.  Corregirá este comportamiento más adelante en este tutorial.  
  
     Si proporciona una respuesta correcta, se abre un cuadro de mensaje, el botón **Iniciar** está disponible y el temporizador se detiene.  
  
### Para continuar o revisar  
  
-   Para ir al siguiente paso del tutorial, vea [Paso 5: Agregar controladores de eventos Enter para los controles NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).  
  
-   Para volver al paso anterior del tutorial, vea [Paso 3: Agregar un temporizador de cuenta atrás](../ide/step-3-add-a-countdown-timer.md).