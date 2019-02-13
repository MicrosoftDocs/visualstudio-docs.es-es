---
title: 'Paso 7: Mantener visibles los pares | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 42e1d08c-7b2e-4efd-9f47-85d6206afe35
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cb65f5b45c34672679f88c7f6ba12f972f0e0388
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54766318"
---
# <a name="step-7-keep-pairs-visible"></a>Paso 7: Mantener visibles los pares
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El juego funciona bien siempre y cuando el jugador elija únicamente parejas de iconos que no coinciden. Sin embargo, piense qué sucedería si el jugador elige una pareja coincidente. En lugar de hacer que los iconos desaparezcan activando el temporizador (con el método `Start()`), el juego se debería restablecer automáticamente para dejar de realizar el seguimiento de las etiquetas mediante las variables de referencia `firstClicked` y `secondClicked`, sin restablecer los colores de las dos etiquetas elegidas.  
  
### <a name="to-keep-pairs-visible"></a>Para mantener las parejas visibles  
  
1.  Agregue la siguiente instrucción `if` al método de control de eventos `label_Click()`, casi al final del código, justo encima de la instrucción donde se inicia el temporizador. Observe el código minuciosamente mientras lo agrega al programa. Observe cómo funciona.  
  
     [!code-csharp[VbExpressTutorial4Step7#9](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step7/cs/form1.cs#9)]
     [!code-vb[VbExpressTutorial4Step7#9](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step7/vb/form1.vb#9)]  
  
     La primera línea de la instrucción `if` que acaba de agregar comprueba si el icono de la primera etiqueta en eligió el jugador es igual que el icono de la segunda etiqueta. Si los iconos son iguales, el programa ejecuta las tres instrucciones entre llaves en C# o las tres instrucciones incluidas en la instrucción `if` en Visual Basic. Las dos primeras instrucciones restablecen las variables de referencia `firstClicked` y `secondClicked` para que ya no realicen el seguimiento de ninguna de las etiquetas. (Quizás reconozca esas dos instrucciones por el controlador de eventos Tick del temporizador). La tercera es una instrucción `return`, que indica al programa que omita el resto de las instrucciones del método sin ejecutarlas.  
  
     Si programa en Visual C#, quizás haya observado que en una parte del código se usa un solo signo de igualdad (`=`), mientras que otras instrucciones usan dos (`==`). Piense por qué se usa `=` en algunos lugares y `==` en otros.  
  
     Aquí tiene un buen ejemplo donde se ve la diferencia. Observe minuciosamente el código que se encuentra entre paréntesis en la instrucción `if`.  
  
    ```vb  
    firstClicked.Text = secondClicked.Text  
    ```  
  
    ```csharp  
    firstClicked.Text == secondClicked.Text  
    ```  
  
     A continuación, examine con detalle la primera instrucción del bloque de código situado después de la instrucción `if`.  
  
    ```vb  
    firstClicked = Nothing  
    ```  
  
    ```csharp  
    firstClicked = null;  
    ```  
  
     La primera de esas dos instrucciones comprueba si dos iconos son iguales. Dado que se comparan dos valores, el programa de Visual C# usa el operador de igualdad `==`. La segunda instrucción en realidad cambia el valor (lo que se conoce como *asignación*), estableciendo la variable de referencia `firstClicked` en `null` para restablecerlo. Por eso se usa en este caso el operador de asignación `=`. Visual C# usa `=` para establecer los valores y `==` para compararlos. En Visual Basic se usa `=` tanto para la asignación de variables como para la comparación.  
  
2.  Guarde y ejecute el programa, y después empiece a elegir iconos del formulario. Si elige una pareja que no coincide, se desencadena el evento Tick del temporizador, y ambos iconos desaparecen. Si elige una pareja coincidente, se ejecuta la nueva instrucción `if` y la instrucción return hace que el método omita el código que inicia el temporizador, de modo que los iconos se mantengan visibles, como se muestra en la siguiente ilustración.  
  
     ![Juego que creará en este tutorial](../ide/media/express-finishedgame.png "Express_FinishedGame")  
Juego de formar parejas con pares de iconos visibles  
  
### <a name="to-continue-or-review"></a>Para continuar o revisar  
  
-   Para ir al paso siguiente del tutorial, consulte [Paso 8: Agregar un método para comprobar si el jugador ganó](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).  
  
-   Para volver al paso anterior del tutorial, vea [Paso 6: Agregar un temporizador](../ide/step-6-add-a-timer.md).
