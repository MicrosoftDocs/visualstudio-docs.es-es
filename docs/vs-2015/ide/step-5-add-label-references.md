---
title: 'Paso 5: Agregar referencias a etiquetas | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d418350c-0396-494e-8149-71fa61b395c5
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2c82e271ef4dcfd1172f8fc386f77681b8f80244
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581774"
---
# <a name="step-5-add-label-references"></a>Paso 5: Agregar referencias a etiquetas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [paso 5: agregar referencias a etiquetas](https://docs.microsoft.com/visualstudio/ide/step-5-add-label-references).  
  
El programa necesita realizar un seguimiento de los controles Label que elige el jugador. De momento, el programa muestra todas las etiquetas elegidas por el jugador. Pero vamos a cambiar eso. Después de que se haga elegido la primera etiqueta, el programa debería mostrar el icono correspondiente. Una vez elegida la segunda etiqueta, el programa debe mostrar ambos iconos durante un breve período de tiempo y después ocultar ambos iconos de nuevo. El programa realizará ahora un seguimiento del control de etiqueta elegido en primer lugar y del control elegido en segundo lugar mediante *variables de referencia*.  
  
### <a name="to-add-label-references"></a>Para agregar referencias de etiqueta  
  
1.  Para agregar referencias de etiqueta a un formulario, use el siguiente código.  
  
     [!code-csharp[VbExpressTutorial4Step5#5](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs#5)]
     [!code-vb[VbExpressTutorial4Step5#5](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb#5)]  
  
     Estas variables de referencia son similares a las instrucciones usadas anteriormente para agregar objetos (por ejemplo, objetos `Timer`, objetos `List` y objetos `Random`) a un formulario. Sin embargo, estas instrucciones no hacen aparecer dos controles de etiqueta adicionales en el formulario porque ninguna de las dos instrucciones incluye la palabra clave `new`. Sin la palabra clave `new`, no se crea ningún objeto. Por ello, `firstClicked` y `secondClicked` se denominan variables de referencia: simplemente realizan un seguimiento o hacen referencia a objetos `Label`.  
  
     Cuando una variable no realiza el seguimiento de ningún objeto, se establece en un valor reservado especial: `null` en Visual C# y `Nothing` en Visual Basic. Por lo tanto, cuando se inicia el programa, el valor de `firstClicked` y el valor de `secondClicked` están establecidos en `null` o `Nothing`, lo que significa que las variables no realizan ningún tipo de seguimiento.  
  
2.  Modifique el controlador de eventos Click para usar la nueva variable de referencia `firstClicked`. Quite la última instrucción del método de control de eventos `label_Click()` (`clickedLabel.ForeColor = Color.Black;`) y reemplácela por la instrucción `if` que figura a continuación. (Asegúrese de incluir el comentario y la instrucción `if` completa).  
  
     [!code-csharp[VbExpressTutorial4Step5#6](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs#6)]
     [!code-vb[VbExpressTutorial4Step5#6](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb#6)]  
  
3.  Guarde y ejecute el programa. Elija uno de los controles de etiqueta y aparecerá el correspondiente icono.  
  
4.  Elija el siguiente control de etiqueta y verá que no sucede nada. El programa ya está realizando un seguimiento de la primera etiqueta que eligió el jugador, por lo que el valor de `firstClicked` no es `null` en Visual C# ni `Nothing` en Visual Basic. Cuando la instrucción `if` comprueba `firstClicked` para determinar si su valor es `null` o `Nothing`, concluye que no tiene ese valor y no ejecuta las instrucciones de la instrucción `if`. Por lo tanto, solo el primer icono elegido se vuelve negro y los demás iconos se vuelven invisibles, tal y como se muestra en la siguiente imagen.  
  
     ![Juego de formar parejas con un icono visible](../ide/media/express-tut4step5.png "Express_Tut4Step5")  
Juego de formar parejas con un icono visible  
  
     Corregirá esta situación en el siguiente paso del tutorial agregando un control **Timer**.  
  
### <a name="to-continue-or-review"></a>Para continuar o revisar  
  
-   Para ir al siguiente paso del tutorial, vea [Paso 6: Agregar un temporizador](../ide/step-6-add-a-timer.md).  
  
-   Para volver al paso previo del tutorial, vea [Paso 4: Agregar un controlador de eventos Click a cada etiqueta](../ide/step-4-add-a-click-event-handler-to-each-label.md).



