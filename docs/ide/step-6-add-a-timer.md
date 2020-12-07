---
title: 'Paso 6: Agregar un temporizador'
description: Aprenda a agregar un control <xref:System.Windows.Forms.Timer> al juego de formar parejas.
ms.custom: SEO-VS-2020
ms.date: 03/31/2020
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 09e7930b-cab6-4a22-9a6f-72e23f489585
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2684b197fc32b33081c8ecdfa8139b3c8f14e752
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480556"
---
# <a name="step-6-add-a-timer"></a>Paso 6: Agregar un temporizador
A continuación, agregará un control <xref:System.Windows.Forms.Timer> al juego de formar parejas. Un temporizador espera un número especificado de milisegundos para desencadenar un evento conocido como *tic*. Esto es útil para iniciar o repetir una acción de forma periódica. En este caso, se usará un temporizador para permitir a los participantes elegir dos iconos y, si no coinciden, ocultarlos de nuevo trascurrido un breve período de tiempo.

## <a name="to-add-a-timer"></a>Para agregar un temporizador

1. En el cuadro de herramientas del **Diseñador de Windows Forms**, pulse **Temporizador** (en la categoría **Componentes**) y, después, la tecla **Entrar** o haga doble clic en el temporizador para agregar un control de temporizador al formulario. El icono del temporizador, denominado **Temporizador1**, debe aparecer en un espacio bajo el formulario, como se muestra en la siguiente imagen.

     ![Temporizador](../ide/media/express_timer.png)<br/>
**_Temporizador_* _

    > [!NOTE]
    > Si el cuadro de herramientas está vacío, asegúrese de seleccionar el diseñador de formularios, y no el código subyacente del formulario, antes de abrir el cuadro de herramientas.

2. Pulse el icono _ *Temporizador1** para seleccionar el temporizador. En la ventana **Propiedades**, cambie de la vista de eventos a la de propiedades. Después, establezca la propiedad **Interval** del temporizador en **750**, pero deje la propiedad **Enabled** establecida en **False**. La propiedad **Interval** indica al temporizador cuánto tiempo debe esperar entre los *tics* o cuando se desencadena el evento <xref:System.Windows.Forms.Timer.Tick>. Un valor de 750 indica al temporizador que espere tres cuartos de segundo (750 milisegundos) antes de desencadenar el evento Tick. Llame al método <xref:System.Windows.Forms.Timer.Start> para iniciar el temporizador únicamente después de que el jugador elija la segunda etiqueta.

3. Pulse el icono del control de temporizador en el **Diseñador de Windows Forms** y pulse la tecla **Entrar**, o haga doble clic en el temporizador, para agregar un controlador de eventos Tic vacío. Reemplace el código por el código siguiente o escriba manualmente el código siguiente en el controlador de eventos.

     [!code-csharp[VbExpressTutorial4Step6#7](../ide/codesnippet/CSharp/step-6-add-a-timer_1.cs)]
     [!code-vb[VbExpressTutorial4Step6#7](../ide/codesnippet/VisualBasic/step-6-add-a-timer_1.vb)]

      > [!IMPORTANT]
      > Use el control del lenguaje de programación situado en la parte superior derecha de esta página para ver el fragmento de código de C# o el de Visual Basic.<br><br>![Control de lenguaje de programación para Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     El controlador de eventos Tic realiza tres operaciones: Primero, se asegura de que el temporizador no está en marcha mediante una llamada al método <xref:System.Windows.Forms.Timer.Stop>. A continuación, usa las dos variables de referencia, `firstClicked` y `secondClicked`, para ocultar de nuevo los iconos de las dos etiquetas que el jugador eligió. Finalmente, restablece las variables de referencia `firstClicked` y `secondClicked` en `null` en C# y `Nothing` en Visual Basic. Este paso es importante porque es como se restablece el programa. Ahora no realiza el seguimiento de ningún control <xref:System.Windows.Forms.Label> y vuelve a estar listo para que el jugador elija otra etiqueta.

    > [!NOTE]
    > Un objeto Timer tiene un método `Start()` que inicia el temporizador y un método `Stop()` que lo detiene. Al establecer la propiedad **Enabled** del temporizador en **True** en la ventana **Propiedades**, inicia los tics nada más comenzar el programa. En cambio, si se deja establecido en **False**, no inicia los tics hasta que se llama a su método `Start()`. Normalmente, un temporizador desencadena su evento Tic una y otra vez usando la propiedad **Interval** para determinar cuántos milisegundos debe esperar entre los tics. Es posible que haya observado cómo se llama al método `Stop()` del temporizador dentro del evento Tick. Esto hace que el temporizador entre en *modo de un disparo*, lo que significa que, cuando se llama al método `Start()`, espera el intervalo especificado, desencadena un único evento Tic y después se para.

4. Para ver el nuevo temporizador en acción, vaya al editor de código y agregue el siguiente código al principio y al final del método de control de eventos `label_Click()`. (Se agregan dos instrucciones `if` al principio y tres instrucciones al final; el resto del método no cambia).

     [!code-csharp[VbExpressTutorial4Step6#8](../ide/codesnippet/CSharp/step-6-add-a-timer_2.cs)]
     [!code-vb[VbExpressTutorial4Step6#8](../ide/codesnippet/VisualBasic/step-6-add-a-timer_2.vb)]

     El código que se encuentra al principio del método comprueba si el temporizador se ha iniciado comprobando el valor de la propiedad **Enabled**. Así, si el jugador elige el primer y segundo control Label y se inicia el temporizador, no sucederá nada al elegir un tercer control. También impide que el jugador haga clic rápidamente una tercera vez antes de que el juego esté listo para otro primer clic. 

     El código al final del método establece la variable de referencia `secondClicked` para que haga el seguimiento del segundo control Label que el jugador eligió y después establece el color del icono de esa etiqueta en negro para que sea visible. A continuación, inicia el temporizador en modo de un disparo de forma que espera durante 750 milisegundos antes de desencadenar un único evento Tick. Es entonces cuando el controlador de eventos Tic del temporizador oculta los dos iconos y restablece las variables de referencia `firstClicked` y `secondClicked` para que el formulario esté listo cuando el jugador pulse otro par de iconos.

5. Guarde y ejecute el programa. Elija un icono y se hará visible.

6. Elija otro icono. Aparece brevemente y, a continuación, ambos iconos desaparecen. Repita el proceso varias veces. Ahora, el formulario realiza el seguimiento del primer y segundo icono que ha elegido y usa el temporizador para crear una pausa antes de hacer que los iconos desaparezcan.

## <a name="to-continue-or-review"></a>Para continuar o revisar

- Para ir al siguiente paso del tutorial, vea **[Paso 7: Mantener visibles los pares](../ide/step-7-keep-pairs-visible.md)** .

- Para volver al paso anterior del tutorial, vea [Paso 5: Agregar referencias a etiquetas](../ide/step-5-add-label-references.md).
