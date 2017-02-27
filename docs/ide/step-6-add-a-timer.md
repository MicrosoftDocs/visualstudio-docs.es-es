---
title: "Paso 6: Agregar un temporizador | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 09e7930b-cab6-4a22-9a6f-72e23f489585
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Paso 6: Agregar un temporizador
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A continuación, agregará un control **Timer** al juego de formar parejas.  Un temporizador espera un número especificado de milisegundos para desencadenar un evento conocido como *tick*.  Esto es útil para iniciar o repetir una acción de forma periódica.  En este caso, se usará un temporizador para permitir a los participantes elegir dos iconos y, si no coinciden, ocultarlos de nuevo trascurrido un breve período de tiempo.  
  
### Para agregar un temporizador  
  
1.  En el cuadro de herramientas del Diseñador de Windows Forms, elija **Timer** \(en la categoría **Componentes**\) y, a continuación, la tecla Entrar o haga doble clic en el temporizador para agregar un control timer al formulario.  El icono del temporizador, denominado **Timer1**, debe aparecer en un espacio bajo del formulario, como se muestra en la siguiente imagen.  
  
     ![Temporizador](../ide/media/express_timer.png "Express\_Timer")  
Temporizador  
  
    > [!NOTE]
    >  Si el cuadro de herramientas está vacío, asegúrese de seleccionar el diseñador de formularios, y no el código subyacente del formulario, antes de abrir el cuadro de herramientas.  
  
2.  Elija el icono **Timer1** para seleccionar el temporizador.  En la ventana **Propiedades**, cambie de la vista de eventos a la de propiedades.  Después, establezca la propiedad **Interval** del temporizador en 750, pero deje la propiedad **Enabled** establecida en **False**.  La propiedad **Interval** indica al temporizador cuánto tiempo debe esperar entre los *pasos* o cuando se desencadena el evento tick.  Un valor de 750 indica al temporizador que espere tres cuartos de segundo \(750 milisegundos\) antes de desencadenar el evento Tick.  Llame al método `Start()` para iniciar el temporizador únicamente después de que el jugador elija la segunda etiqueta.  
  
3.  Elija el icono del control de temporizador en el Diseñador de Windows Forms y elija la tecla ENTRAR, o haga doble clic en el temporizador, para agregar un controlador de eventos **Tick** vacío.  Reemplace el código por el código siguiente o escriba manualmente el código siguiente en el controlador de eventos.  
  
     [!code-cs[VbExpressTutorial4Step6#7](../ide/codesnippet/CSharp/step-6-add-a-timer_1.cs)]
     [!code-vb[VbExpressTutorial4Step6#7](../ide/codesnippet/VisualBasic/step-6-add-a-timer_1.vb)]  
  
     El controlador de eventos Tick realiza tres acciones: primero, se asegura de que el temporizador no está en marcha mediante una llamada al método `Stop()`.  A continuación, usa las dos variables de referencia, `firstClicked` y `secondClicked`, para ocultar de nuevo los iconos de las dos etiquetas que el jugador eligió.  Finalmente, restablece las variables de referencia `firstClicked` y `secondClicked` en `null` en Visual C\# y `Nothing` en Visual Basic.  Este paso es importante porque es como se restablece el programa.  Ahora no realiza el seguimiento de ningún control `Label` y vuelve a estar listo para que el jugador elija otra etiqueta.  
  
    > [!NOTE]
    >  Un objeto `Timer` tiene un método `Start()` que inicia el temporizador y un método `Stop()` que lo detiene.  Al establecer la propiedad **Enabled** del temporizador en **True** en la ventana **Propiedades**, inicia los pasos nada más comenzar el programa.  Sin embargo, si se deja establecido en **False**, no inicia los pasos hasta que se llama a su método `Start()`.  Normalmente, un temporizador desencadena su evento Tick una y otra vez utilizando la propiedad **Interval** para determinar cuántos milisegundos debe esperar entre los pasos.  Es posible que haya observado cómo se llama al método `Stop()` del temporizador dentro del evento Tick.  Esto hace que el temporizador entre en *modo de un disparo*, lo que significa que, cuando se llama al método `Start()`, espera el intervalo especificado, desencadena un único evento Tick y después se para.  
  
4.  Para ver el nuevo temporizador en acción, vaya al editor de código y agregue el siguiente código al principio y al final del método de control de eventos `label_Click()`. \(Se agrega una instrucción `if` al principio y tres instrucciones al final; el resto del método no cambia\).  
  
     [!code-cs[VbExpressTutorial4Step6#8](../ide/codesnippet/CSharp/step-6-add-a-timer_2.cs)]
     [!code-vb[VbExpressTutorial4Step6#8](../ide/codesnippet/VisualBasic/step-6-add-a-timer_2.vb)]  
  
     El código que se encuentra al principio del método comprueba si el temporizador se inició comprobando el valor de la propiedad **Enabled**.  Así, si el jugador elige el primer y segundo control `Label` y se inicia el temporizador, no sucederá nada al elegir un tercer control.  
  
     El código al final del método establece la variable de referencia `secondClicked` para que haga el seguimiento del segundo control `Label` que el jugador eligió y después establece el color del icono de esa etiqueta en negro para que sea visible.  A continuación, inicia el temporizador en modo de un disparo de forma que espera durante 750 milisegundos antes de desencadenar un único evento Tick.  Es entonces cuando el controlador de eventos Tick del temporizador oculta los dos iconos y restablece las variables de referencia `firstClicked` y `secondClicked` para que el formulario esté listo cuando el jugador elija otro par de iconos.  
  
5.  Guarde y ejecute el programa.  Elija un icono y se hará visible.  
  
6.  Elija otro icono.  Aparece brevemente y, a continuación, ambos iconos desaparecen.  Repita el proceso varias veces.  Ahora, el formulario realiza el seguimiento del primer y segundo icono que ha elegido y usa el temporizador para crear una pausa antes de hacer que los iconos desaparezcan.  
  
### Para continuar o revisar  
  
-   Para ir al siguiente paso del tutorial, vea [Paso 7: Mantener visibles los pares](../ide/step-7-keep-pairs-visible.md).  
  
-   Para volver al paso anterior del tutorial, vea [Paso 5: Agregar referencias a etiquetas](../ide/step-5-add-label-references.md).