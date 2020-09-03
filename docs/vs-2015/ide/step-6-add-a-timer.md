---
title: 'Paso 6: Agregar un temporizador | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 09e7930b-cab6-4a22-9a6f-72e23f489585
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6a2d47a66cdedfc191212a178221712de6aefa61
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671698"
---
# <a name="step-6-add-a-timer"></a>Paso 6: Agregar un temporizador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A continuación, agregará un control **Temporizador** al juego de formar parejas. Un temporizador espera un número especificado de milisegundos para desencadenar un evento conocido como *tic*. Esto es útil para iniciar o repetir una acción de forma periódica. En este caso, se usará un temporizador para permitir a los participantes elegir dos iconos y, si no coinciden, ocultarlos de nuevo trascurrido un breve período de tiempo.

### <a name="to-add-a-timer"></a>Para agregar un temporizador

1. En el cuadro de herramientas de Diseñador de Windows Forms, elija **temporizador** (en la categoría **componentes** ) y, a continuación, elija la tecla entrar o haga doble clic en el temporizador para agregar un control Timer al formulario. El icono del temporizador, denominado **Temporizador1**, debe aparecer en un espacio bajo el formulario, como se muestra en la siguiente imagen.

     ![Temporizador](../ide/media/express-timer.png "Express_Timer") de Temporizador

    > [!NOTE]
    > Si el cuadro de herramientas está vacío, asegúrese de seleccionar el diseñador de formularios, y no el código subyacente del formulario, antes de abrir el cuadro de herramientas.

2. Pulse el icono **Temporizador1** para seleccionar el temporizador. En la ventana **Propiedades**, cambie de la vista de eventos a la de propiedades. Después, establezca la propiedad **Interval** del temporizador en **750**, pero deje la propiedad **Enabled** establecida en **False**. La propiedad **Interval** indica al temporizador cuánto tiempo debe esperar entre los *tics* o cuando se desencadena el evento Tic. Un valor de 750 indica al temporizador que espere tres cuartos de segundo (750 milisegundos) antes de desencadenar el evento Tick. Llame al método `Start()` para iniciar el temporizador únicamente después de que el jugador elija la segunda etiqueta.

3. Elija el icono control de temporizador en Diseñador de Windows Forms y, a continuación, elija la tecla entrar o haga doble clic en el temporizador para agregar un controlador de eventos **tick** vacío. Reemplace el código por el código siguiente o escriba manualmente el código siguiente en el controlador de eventos.

     [!code-csharp[VbExpressTutorial4Step6#7](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step6/cs/form1.cs#7)]
     [!code-vb[VbExpressTutorial4Step6#7](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step6/vb/form1.vb#7)]

     El controlador de eventos Tic realiza tres operaciones: Primero, se asegura de que el temporizador no está en marcha mediante una llamada al método `Stop()`. A continuación, usa las dos variables de referencia, `firstClicked` y `secondClicked`, para ocultar de nuevo los iconos de las dos etiquetas que el jugador eligió. Finalmente, restablece las variables de referencia `firstClicked` y `secondClicked` en `null` en Visual C# y `Nothing` en Visual Basic. Este paso es importante porque es como se restablece el programa. Ahora no realiza el seguimiento de ningún control `Label` y vuelve a estar listo para que el jugador elija otra etiqueta.

    > [!NOTE]
    > Un objeto `Timer` tiene un método `Start()` que inicia el temporizador y un método `Stop()` que lo detiene. Al establecer la propiedad **Enabled** del temporizador en **True** en la ventana **Propiedades**, inicia los tics nada más comenzar el programa. En cambio, si se deja establecido en **False**, no inicia los tics hasta que se llama a su método `Start()`. Normalmente, un temporizador desencadena su evento Tic una y otra vez usando la propiedad **Interval** para determinar cuántos milisegundos debe esperar entre los tics. Es posible que haya observado cómo se llama al método `Stop()` del temporizador dentro del evento Tick. Esto hace que el temporizador entre en *modo de un disparo*, lo que significa que, cuando se llama al método `Start()`, espera el intervalo especificado, desencadena un único evento Tic y después se para.

4. Para ver el nuevo temporizador en acción, vaya al editor de código y agregue el siguiente código al principio y al final del método de control de eventos `label_Click()`. (Se agrega una instrucción `if` al principio y tres instrucciones al final; el resto del método no cambia).

     [!code-csharp[VbExpressTutorial4Step6#8](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step6/cs/form1.cs#8)]
     [!code-vb[VbExpressTutorial4Step6#8](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step6/vb/form1.vb#8)]

     El código que se encuentra al principio del método comprueba si el temporizador se ha iniciado comprobando el valor de la propiedad **Enabled**. Así, si el jugador elige el primer y segundo control `Label` y se inicia el temporizador, no sucederá nada al elegir un tercer control.

     El código al final del método establece la variable de referencia `secondClicked` para que haga el seguimiento del segundo control `Label` que el jugador ha elegido y después establece el color del icono de esa etiqueta en negro para que sea visible. A continuación, inicia el temporizador en modo de un disparo de forma que espera durante 750 milisegundos antes de desencadenar un único evento Tick. Es entonces cuando el controlador de eventos Tick del temporizador oculta los dos iconos y restablece las variables de referencia `firstClicked` y `secondClicked` para que el formulario esté listo cuando el jugador elija otro par de iconos.

5. Guarde y ejecute el programa. Elija un icono y se hará visible.

6. Elija otro icono. Aparece brevemente y, a continuación, ambos iconos desaparecen. Repita el proceso varias veces. Ahora, el formulario realiza el seguimiento del primer y segundo icono que ha elegido y usa el temporizador para crear una pausa antes de hacer que los iconos desaparezcan.

### <a name="to-continue-or-review"></a>Para continuar o revisar

- Para ir al siguiente paso del tutorial, vea [paso 7: mantener visibles los pares](../ide/step-7-keep-pairs-visible.md).

- Para volver al paso anterior del tutorial, vea [paso 5: agregar referencias de etiqueta](../ide/step-5-add-label-references.md).
