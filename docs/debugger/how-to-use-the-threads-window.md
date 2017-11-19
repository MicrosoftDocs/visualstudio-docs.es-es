---
title: "Depurar una aplicación multiproceso mediante la ventana subprocesos | Documentos de Microsoft"
ms.custom: H1HackMay2017
ms.date: 05/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
caps.latest.revision: "38"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4469f2f70bececca258fe4ea1a98d753f8349f87
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-debug-a-multithreaded-application-in-visual-studio-using-the-threads-window"></a>Tutorial: Depurar una aplicación multiproceso en Visual Studio mediante la ventana subprocesos
Visual Studio proporciona un **subprocesos** ventana y otra interfaz de usuario elementos para ayudar a depurar aplicaciones multiproceso. Este tutorial muestra cómo utilizar el **subprocesos** ventana y **ubicación de depuración** barra de herramientas. Para obtener información acerca de las otras herramientas, vea [empezar a depurar aplicaciones multiproceso](../debugger/get-started-debugging-multithreaded-apps.md). Este tutorial dura sólo unos minutos, pero completarlo, se familiarizará con las características para depurar aplicaciones multiproceso.   
  
Para empezar este tutorial, necesita un proyecto de aplicación multiproceso. Siga los pasos que se enumeran a continuación para crear dicho proyecto.  
  
#### <a name="to-create-the-multithreaded-app-project"></a>Para crear el proyecto de aplicación multiproceso  
  
1.  En el **archivo** menú, elija **New** y, a continuación, haga clic en **proyecto**.  
  
     Aparecerá el cuadro de diálogo **Nuevo proyecto** .  
  
2.  En el **tipo de proyecto**s cuadro, haga clic en el idioma de su elección: **Visual Basic**, **Visual C#**, o **Visual C++**.  
  
3.  En el **plantillas** cuadro, elija **aplicación de consola**.  
  
4.  En el **nombre** cuadro, escriba el nombre MyThreadWalkthroughApp.  
  
5.  Haga clic en **Aceptar**.  
  
     Aparecerá un nuevo proyecto de consola. Una vez creado el proyecto, aparecerá un archivo de código fuente. Dependiendo del lenguaje elegido, el archivo de código fuente podría denominarse Module1.vb, Program.cs o MyThreadWalkthroughApp.cpp.  
  
6.  Elimine el código que aparece en el archivo de origen y reemplácelo con el código de ejemplo que aparece en la sección "Crear un subproceso" del tema [crear subprocesos y pasar datos en tiempo de inicio](/dotnet/standard/threading/creating-threads-and-passing-data-at-start-time).  
  
7.  En el **archivo** menú, haga clic en **guardar todo**.  
  
#### <a name="to-begin-the-tutorial"></a>Para comenzar el tutorial  
  
-   En el editor de código fuente, busque el código siguiente:  
  
    ```VB  
    Thread.Sleep(3000)   
    Console.WriteLine(  
    ```  
  
    ```CSharp  
    Thread.Sleep(3000);  
    Console.WriteLine();  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    Console.WriteLine();  
    ```  
  
#### <a name="to-start-debugging"></a>Para iniciar la depuración  
  
1.  Haga clic en el margen interno izquierdo de la `Console.WriteLine` instrucción para insertar un nuevo punto de interrupción.  
  
     En el margen interno en el lado izquierdo del editor de código fuente, aparece un círculo rojo. Esto indica que ahora hay un punto de interrupción en esa ubicación.  
  
2.  En el **depurar** menú, haga clic en **Iniciar depuración** (**F5**).  
  
     La depuración comenzará, la aplicación de consola empezará a ejecutarse y se detendrá en el punto de interrupción.  
  
3.  Si la ventana de la aplicación de consola tiene el foco en ese punto, haga clic en la ventana de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para que el foco vuelva a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  En el editor de código fuente, busque la línea que contiene el código siguiente:  
  
    ```VB  
    Thread.Sleep(5000)   
    ```  
  
    ```CSharp  
    Thread.Sleep(3000);  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    ```
  
#### <a name="to-discover-the-thread-marker"></a>Para detectar el marcador de subproceso  

1.  En la barra de herramientas Depurar, haga clic en el **Mostrar subprocesos en código fuente** botón ![Mostrar subprocesos en código fuente](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker"). 
  
2.  Examine el margen interno izquierdo de la ventana. En esta línea, verá un *marcador de subproceso* icono ![marcador de subproceso](../debugger/media/dbg-thread-marker.png "ThreadMarker") que es similar a dos hilos. El marcador de subproceso indica que un subproceso se ha detenido en esa ubicación.  
  
3.  Desplace el puntero sobre el marcador de subproceso. Aparece la Información sobre datos. En ella se indican el nombre y el número de id. de subproceso de cada subproceso detenido. En este caso, sólo hay un subproceso, cuyo nombre probablemente es `<noname>`.  

    > [!TIP]
    > Le resultará útil para identificar subprocesos sin nombre cambiándole. En la ventana subprocesos, elija **cambiar el nombre de** después el botón secundario en el **nombre** columna en la fila de subprocesos.
  
4.  Haga clic en el marcador de subproceso para ver las opciones disponibles en el menú contextual. 
    
  
## <a name="flagging-and-unflagging-threads"></a>Marcar y quitar marcadores de subprocesos  
Puede marcar los subprocesos que desea prestar atención especial. Acción de marcar subprocesos es una buena forma de realizar un seguimiento de los subprocesos importantes y obviar los que no le interesan.  
  
#### <a name="to-flag-threads"></a>Para marcar subprocesos   

1.  En **vista** menú, elija **las barras de herramientas**.  
  
    Asegúrese de que el **ubicación de depuración** barra de herramientas está seleccionada.

2.  Vaya a la **ubicación de depuración** barra de herramientas y haga clic en el **subprocesos** lista.  
  
    > [!NOTE]
    >  Puede reconocer esta barra de herramientas mediante tres listas destacadas: **proceso**, **subprocesos**, y **marco de pila**.  
  
3.  Observe cuántos subprocesos aparecen en la lista.  
  
4.  Vaya al editor de código fuente y haga clic en el marcador de subproceso ![marcador de subproceso](../debugger/media/dbg-thread-marker.png "ThreadMarker") nuevo.  
  
5.  En el menú contextual, seleccione **marca**y, a continuación, haga clic en el nombre del subproceso y el número de ID.  
  
6.  Vuelva a **ubicación de depuración** barra de herramientas y busque el **mostrar sólo subprocesos marcados** icono ![Mostrar subprocesos marcados](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker") a la derecha de la **subprocesos** lista.  
  
    El icono de marcas en el botón aparecía antes atenuado. Ahora, es un botón activo.  
  
7.  Haga clic en el **mostrar sólo subprocesos marcados** icono.  
  
    Sólo el subproceso marcado aparece ahora en la lista. (Puede hacer clic en el botón de marca única para volver al **mostrar todos los subprocesos** modo.)

8. Abra la ventana subprocesos eligiendo **Depurar > Windows > subprocesos**.

    ![Ventana de subprocesos](../debugger/media/dbg-threads-window.png "ThreadsWindow")  
  
    En el **subprocesos** ventana, el subproceso marcado tiene un icono de marcador rojo destacado asociado a él.

    > [!TIP]
    > Cuando se han marcado algunos subprocesos, puede haga clic en una línea de código en el editor de código y elija **ejecutar subprocesos marcados hasta el Cursor** (asegúrese de que elige llegará a todos los subprocesos marcan de código). Esto pausará al número de subprocesos en la línea seleccionada del código, lo que hace más fácil controlar el orden de ejecución por [inmovilizar y reanudar subprocesos](#bkmk_freeze).
  
11. En el editor de código fuente, haga clic en el marcador de subproceso.  
  
     Fíjese en las opciones que ahora están disponibles en el menú contextual. En lugar de **marca**, verá ahora **Quitar marcador**. No haga clic en **Quitar marcador**.  

     Para obtener información sobre cómo quitar marcadores de subprocesos, vaya al procedimiento siguiente.  
  
#### <a name="to-unflag-threads"></a>Para quitar marcadores de subprocesos  
  
1.  En el **subprocesos** ventana, haga clic en la línea que corresponde al subproceso marcado.  
  
     Se mostrará un menú contextual. Tiene las opciones **Quitar marcador** y **desmarcar todos los subprocesos**.  
  
2.  Para quitar el marcador del subproceso, haga clic en **Quitar marcador**.  

    Mire el **ubicación de depuración** barra de herramientas de nuevo. El **mostrar sólo subprocesos marcados** botón está atenuado de nuevo. Ha quitado el marcador del único subproceso marcado. Dado que no hay ningún subproceso marcado, la barra de herramientas ha regresado al **mostrar todos los subprocesos** modo. Haga clic en el **subprocesos** lista y compruebe que puede ver todos los subprocesos.  
  
5.  Vuelva a la **subprocesos** ventana y examine las columnas de información.  
  
    En la primera columna, verá un icono de esquema de marca en cada fila de la lista de subprocesos. (El contorno significa que el subproceso no está marcado).  
  
6.  Haga clic en los iconos de esquema de la marca de dos subprocesos, el segundo y tercero empezando por la parte inferior de la lista. 

    Los iconos de marcador se vuelven de color rojo sólido, en lugar de mostrarse como contornos huecos.  
  
7.  Haga clic en el botón situado en la parte superior de la columna de marcadores.  
  
    El orden de la lista de subprocesos cambia al hacer clic en el botón. La lista de subprocesos está ordenada ahora con los subprocesos marcados al principio de la misma.  
  
8.  Haga clic otra vez en el botón situado en la parte superior de la columna de marcadores.  
  
    El criterio de ordenación vuelve a cambiar.  
  
## <a name="more-about-the-threads-window"></a>Más información sobre la ventana Subprocesos  
  
#### <a name="to-learn-more-about-the-threads-window"></a>Para obtener más información sobre la ventana Subprocesos  
  
1.  En el **subprocesos** ventana, examine la tercera columna de la izquierda. El botón en la parte superior de esta columna indica **identificador**.  
  
2.  Haga clic en **identificador**.  
  
     La lista de subprocesos estará ordenada ahora por el número de identificación.  
  
3.  Haga clic con el botón secundario en cualquier subproceso de la lista. En el menú contextual, haga clic en **presentación Hexadecimal**.  
  
     Cambiará el formato del número de id. de subproceso.  
  
4.  Desplace el puntero del mouse sobre la **ubicación** columna para cualquier subproceso de la lista.  
  
     Después de un retraso momentáneo, aparece una información sobre datos. Muestra una pila de llamadas parcial para el subproceso.

     > [!TIP]
     > Para obtener una vista gráfica de las pilas de llamadas de subprocesos, abra el [pilas paralelas](../debugger/using-the-parallel-stacks-window.md) ventana (durante la depuración, elija **Debug / Windows / pilas paralelas**).  
  
5.  Examine la cuarta columna de la izquierda, que tiene la etiqueta **categoría**. Los subprocesos están clasificados en categorías.  
  
     El primer subproceso creado en un proceso se conoce como subproceso principal. Búsquelo en la lista de subprocesos.  
  
6.  Haga clic en el subproceso principal y, a continuación, haga clic en **cambiar a subproceso**.  
  
     A **modo de interrupción** aparecerá la ventana. Indica que el depurador no está ejecutando actualmente cualquier código que puede mostrar (porque es el subproceso principal).   
  
7.  Mire el **pila de llamadas** ventana y **ubicación de depuración** barra de herramientas.  
  
     El contenido de la **pila de llamadas** ventana han cambiado. 

## <a name="bkmk_freeze"></a>Inmovilizar y reanudar la ejecución de subprocesos 

Puede inmovilizar y reanudar (suspender y reanudar) los subprocesos para controlar el orden en el que los subprocesos realizan trabajo. Esto puede ayudarle a resolver problemas de simultaneidad, como interbloqueos y condiciones de anticipación.

> [!TIP]
> Si desea seguir un único subproceso sin inmovilizar otros subprocesos (también un escenario de depuración comunes), vea [empezar a depurar aplicaciones multiproceso](../debugger/get-started-debugging-multithreaded-apps.md#bkmk_follow_a_thread).
  
#### <a name="to-freeze-and-unfreeze-threads"></a>Para inmovilizar y descongelar subprocesos  
  
1.  En el **subprocesos** ventana, haga clic en cualquier subproceso y, a continuación, haga clic en **inmovilizar**.  
  
2.  Examine la segunda columna (la columna de subproceso actual). El icono de pausa ahora aparece en él. Esos icono de pausa indica que el subproceso está inmovilizado.  
  
3.  Mostrar la **número de suspendidos** columna seleccionándola en la **columnas** lista.

    El recuento de suspensión del subproceso ahora es 1.  
  
4.  Haga clic en el subproceso inmovilizado y, a continuación, haga clic en **reanudar**.  
  
     La columna del subproceso actual y la **número de suspendidos** cambio de columna. 
  
## <a name="switching-the-to-another-thread"></a>Cambiar el a otro subproceso 
  
#### <a name="to-switch-threads"></a>Para cambiar subprocesos  
  
1.  En el **subprocesos** ventana, examine la segunda columna de la izquierda (la columna de subproceso actual). El botón situado en la parte superior de esta columna no tiene ningún texto o icono.
  
2.  Examine la columna del subproceso actual y tenga en cuenta que un subproceso tiene una flecha amarilla. La flecha amarilla indica que este subproceso es el subproceso actual (esta es la ubicación actual del puntero de ejecución).
  
    Tome nota del número de Id. de subproceso donde se ve el icono de subproceso actual. Se moverá el icono de subproceso actual a otro subproceso, pero tendrá que colocarlo de nuevo cuando haya terminado. 
  
3.  Haga clic en otro subproceso y, a continuación, haga clic en **cambiar a subproceso**.  
  
4.  Mire el **pila de llamadas** ventana en el editor de código fuente. El contenido ha cambiado.  
  
5.  Mire el **ubicación de depuración** barra de herramientas. El icono de subproceso actual ha cambiado ahí demasiado.  
  
6.  Vaya a la **ubicación de depuración** barra de herramientas. Seleccione un subproceso distinto de la **subproceso** lista.  
  
7.  Mire el **subprocesos** ventana. El icono de subproceso actual ha cambiado.  
  
8. En el editor de código fuente, haga clic en un marcador de subproceso. En el menú contextual, seleccione **cambiar a subproceso** y haga clic en un número de identificador/nombre de subproceso.  
  
     Ya ha visto tres maneras de cambiar el icono de subproceso actual a otro subproceso: mediante la **subprocesos** ventana, el **subproceso** lista en la **ubicación de depuración** barra de herramientas y la marcador de subproceso en el editor de código fuente.  
  
     Con el marcador de subproceso, puede cambiar sólo a los subprocesos que se detienen en esa ubicación concreta. Mediante el uso de la **subprocesos** ventana y **ubicación de depuración** barra de herramientas, puede cambiar a cualquier subproceso.   
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Cómo: Cambiar a otro subproceso durante la depuración](../debugger/how-to-switch-to-another-thread-while-debugging.md)