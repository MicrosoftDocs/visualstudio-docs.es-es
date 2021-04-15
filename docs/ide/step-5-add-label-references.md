---
title: 'Paso 5: Agregar referencias a etiquetas'
description: Aprenda a agregar referencias de etiqueta a un formulario.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: d418350c-0396-494e-8149-71fa61b395c5
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 393f71c3360371122e86dc078aaa97c6963db325
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2021
ms.locfileid: "107296279"
---
# <a name="step-5-add-label-references"></a>Paso 5: Agregar referencias a etiquetas
El programa necesita realizar un seguimiento de los controles Label que elige el jugador. De momento, el programa muestra todas las etiquetas elegidas por el jugador. Pero vamos a cambiar eso. Después de que se haga elegido la primera etiqueta, el programa debería mostrar el icono correspondiente. Una vez elegida la segunda etiqueta, el programa debe mostrar ambos iconos durante un breve período de tiempo y después ocultar ambos iconos de nuevo. El programa realizará ahora un seguimiento del control Label elegido en primer lugar y del control elegido en segundo lugar mediante *variables de referencia*.

## <a name="to-add-label-references"></a>Para agregar referencias de etiqueta

1. Para agregar referencias de etiqueta a un formulario, use el siguiente código.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb" id="Snippet5":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs" id="Snippet5":::

     > [!IMPORTANT]
     > Use el control del lenguaje de programación situado en la parte superior derecha de esta página para ver el fragmento de código de C# o el de Visual Basic.<br><br>![Control de lenguaje de programación para Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     Estas variables de referencia son similares a las instrucciones usadas anteriormente para agregar objetos (por ejemplo, objetos <xref:System.Windows.Forms.Timer>, objetos <xref:System.Collections.Generic.List%601> y objetos <xref:System.Random>) a un formulario. Sin embargo, estas instrucciones no hacen aparecer dos controlesLabel adicionales en el formulario porque ninguna de las dos instrucciones incluye la palabra clave `new`. Sin la palabra clave `new`, no se crea ningún objeto. Por ello, `firstClicked` y `secondClicked` se denominan variables de referencia: simplemente realizan un seguimiento o hacen referencia a objetos de etiqueta.

     Cuando una variable no realiza el seguimiento de ningún objeto, se establece en un valor reservado especial: `null` en C# y `Nothing` en Visual Basic. Por lo tanto, cuando se inicia el programa, el valor de `firstClicked` y el valor de `secondClicked` están establecidos en `null` o `Nothing`, lo que significa que las variables no realizan ningún tipo de seguimiento.

2. Modifique el controlador de eventos <xref:System.Windows.Forms.Control.Click> para usar la nueva variable de referencia `firstClicked`. Quite la última instrucción del método de control de eventos `label_Click()` (`clickedLabel.ForeColor = Color.Black;`) y reemplácela por la instrucción `if` que figura a continuación. (Asegúrese de incluir el comentario y la instrucción `if` completa).

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb" id="Snippet6":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs" id="Snippet6":::

3. Guarde y ejecute el programa. Elija uno de los controles de etiqueta y aparecerá el correspondiente icono.

4. Elija el siguiente control de etiqueta y verá que no sucede nada. El programa ya está realizando un seguimiento de la primera etiqueta que eligió el jugador, por lo que el valor de `firstClicked` no es `null` en C# ni `Nothing` en Visual Basic. Cuando la instrucción `if` comprueba `firstClicked` para determinar si su valor es `null` o `Nothing`, concluye que no tiene ese valor y no ejecuta las instrucciones de la instrucción `if`. Por lo tanto, solo el primer icono elegido se vuelve negro y los demás iconos se vuelven invisibles, tal y como se muestra en la siguiente imagen.

     ![Juego de formar parejas con un icono visible](../ide/media/express_tut4step5.png)<br/>
***Juego de formar parejas** _ _con un icono visible*

     Corregirá esta situación en el siguiente paso del tutorial agregando un control **Timer**.

## <a name="to-continue-or-review"></a>Para continuar o revisar

- Para ir al siguiente paso del tutorial, consulte **[Paso 6: Agregar un temporizador](../ide/step-6-add-a-timer.md)** .

- Para volver al paso previo del tutorial, vea [Paso 4: Agregar un controlador de eventos Click a cada etiqueta](../ide/step-4-add-a-click-event-handler-to-each-label.md).
