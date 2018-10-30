---
title: 'Tutorial: Depurar una aplicación multiproceso | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- multithreaded debugging, walkthrough
- walkthroughs, multithreaded debugging
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
caps.latest.revision: 42
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 853719e66bf7cd6a258bc2df231ca04fca7a9242
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49884906"
---
# <a name="walkthrough-debugging-a-multithreaded-application"></a>Tutorial: Depurar una aplicación multiproceso
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] Proporciona una mejor **subprocesos** mejoras para facilitar la depuración de aplicaciones multiproceso de la interfaz de ventana y otro usuario. Este tutorial dura sólo unos minutos, pero al completarlo, se familiarizará con las nuevas características de la interfaz para depurar aplicaciones multiproceso.  
  
 Para comenzar el tutorial necesita un proyecto de aplicación multiproceso. Siga los pasos que se enumeran a continuación para crear dicho proyecto.  
  
#### <a name="to-create-the-walkthrough-project"></a>Para crear el proyecto para el tutorial  
  
1.  En el **archivo** menú, elija **New** y, a continuación, haga clic en **proyecto**.  
  
     Aparecerá el cuadro de diálogo **Nuevo proyecto** .  
  
2.  En el **tipo de proyecto**s cuadro, haga clic en el idioma que prefiera: **Visual Basic**, **Visual C#**, o **Visual C++**.  
  
3.  En el **plantillas** , seleccione **aplicación de consola** o **aplicación de consola CLR**.  
  
4.  En el **nombre** cuadro, escriba el nombre MyThreadWalkthroughApp.  
  
5.  Haga clic en **Aceptar**.  
  
     Aparecerá un nuevo proyecto de consola. Una vez creado el proyecto, aparecerá un archivo de código fuente. Dependiendo del lenguaje elegido, el archivo de código fuente podría denominarse Module1.vb, Program.cs o MyThreadWalkthroughApp.cpp.  
  
6.  Elimine el código que aparece en el archivo de origen y reemplazarlo por el código de ejemplo que aparece en la sección "Crear un subproceso" del tema [crear subprocesos y pasar datos en tiempo de inicio](http://msdn.microsoft.com/library/52b32222-e185-4f42-91a7-eaca65c0ab6d).  
  
7.  En el **archivo** menú, haga clic en **guardar todo**.  
  
#### <a name="to-begin-the-walkthrough"></a>Para comenzar el tutorial  
  
-   En la ventana de código fuente, busque el código siguiente:  
  
    ```vb  
    Thread.Sleep(3000)   
    Console.WriteLine(  
    ```  
  
```csharp  
Thread.Sleep(3000);  
Console.WriteLine();  
```  
  
```cpp  
Thread::Sleep(3000);  
Console.WriteLine();  
```  
  
#### <a name="to-start-debugging"></a>Para iniciar la depuración  
  
1.  Haga clic en el `Console.WriteLine` (instrucción), seleccione **punto de interrupción** y, a continuación, haga clic en **Insertar punto de interrupción**.  
  
     En el margen interno izquierdo de la ventana de código fuente, aparecerá una círculo rojo. Esto indica que ahora hay un punto de interrupción en esa ubicación.  
  
2.  En el menú **Depurar**, haga clic en **Iniciar depuración**.  
  
     La depuración comenzará, la aplicación de consola empezará a ejecutarse y se detendrá en el punto de interrupción.  
  
3.  Si la ventana de la aplicación de consola tiene el foco en ese punto, haga clic en la ventana de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para que el foco vuelva a [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4.  En la ventana de código fuente, busque la línea que contiene el código siguiente:  
  
    ```vb  
    Thread.Sleep(5000)   
    ```  
  
```csharp  
Thread.Sleep(3000);  
```  
  
```cpp  
Thread::Sleep(3000);  
```  
  
1.  
  
#### <a name="to-discover-the-thread-marker"></a>Para detectar el marcador de subproceso  
  
1. Haga clic en el **subprocesos** ventana, a continuación, haga clic en **Mostrar subprocesos en código fuente**.  
  
2. Examine el margen interno izquierdo de la ventana. En esa línea, verá un icono que se asemeja a dos hilos. Uno es rojo y el otro azul. El marcador de subproceso indica que un subproceso se ha detenido en esa ubicación. Posiblemente, el subproceso estará detenido en esa ubicación.  
  
3. Desplace el puntero sobre el marcador de subproceso. Aparece una información sobre datos. En ella se indican el nombre y el número de id. de subproceso de cada subproceso detenido. En este caso, sólo hay un subproceso, cuyo nombre probablemente es `<noname>`.  
  
4. Haga clic con el botón secundario en el marcador de subproceso. Fíjese en las opciones del menú contextual.  
  
   Este icono es un *marcador de subproceso*:  
  
   ![Marcador de subproceso](../debugger/media/threadmarker.gif "ThreadMarker")  
  
## <a name="flagging-and-unflagging-threads"></a>Marcar y quitar marcadores de subprocesos  
 En [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)], puede marcar los subprocesos a los que desee prestar una especial atención. La acción de marcar subprocesos es una buena forma de hacer un seguimiento de los subprocesos importantes y obviar los que no interesen.  
  
#### <a name="to-flag-threads"></a>Para marcar subprocesos  
  
1.  En **vista** menú, elija **las barras de herramientas**.  
  
     Asegúrese de que el **ubicación de depuración** barra de herramientas está seleccionado.  
  
2.  Vaya a la **ubicación de depuración** barra de herramientas y haga clic en el **subprocesos** lista.  
  
    > [!NOTE]
    >  Puede reconocer esta barra de herramientas mediante tres listas destacadas: **proceso**, **subprocesos**, y **marco de pila**.  
  
3.  Observe cuántos subprocesos aparecen en la lista.  
  
4.  Vuelva a la ventana de código fuente y contextual el **subprocesos** marcador nuevo.  
  
5.  En el menú contextual, elija **marca**y, a continuación, haga clic en el nombre de subproceso y el número de identificador.  
  
6.  Vuelva a **ubicación de depuración** barra de herramientas y haga clic en el **subprocesos** vuelva a enumerar.  
  
     Sólo el subproceso marcado aparece ahora en la lista. El botón de marca inmediatamente a la derecha de la **subprocesos** lista. El icono de marcador en el botón aparecía antes atenuado. Ahora se muestra en color rojo brillante sólido.  
  
7.  Desplace el puntero sobre el icono de marcador.  
  
     Aparecerá un elemento emergente. Este elemento indica qué modo la **subprocesos** lista se encuentra en: **mostrar sólo subprocesos marcados**.  
  
8.  Haga clic en el botón de marcador para volver al **mostrar todos los subprocesos** modo.  
  
9. Haga clic en el **subprocesos** vuelva a enumerar y comprobar que ahora puede ver todos los subprocesos de nuevo.  
  
10. Haga clic en el botón de marcador para volver al **mostrar sólo subprocesos marcados**.  
  
11. En el **depurar** menú, elija **Windows** y, a continuación, haga clic en **subprocesos**.  
  
     El **subprocesos** aparecerá la ventana. Un subproceso tendrá asociado un icono de marcador destacado.  
  
12. En la ventana de código fuente, vuelva a hacer clic con el botón secundario en el marcador de subproceso.  
  
     Fíjese en las opciones que ahora están disponibles en el menú contextual. En lugar de **marca**, verá ahora **Quitar marcador**. Haga clic en no **Quitar marcador**.  
  
13. Vaya al siguiente procedimiento sobre cómo quitar marcadores de subprocesos.  
  
#### <a name="to-unflag-threads"></a>Para quitar marcadores de subprocesos  
  
1.  En el **subprocesos** ventana, haga clic en la línea que corresponde al subproceso marcado.  
  
     Se mostrará un menú contextual. Tiene opciones para **Quitar marcador** y **marcador de todos los**.  
  
2.  Para quitar el marcador del subproceso, haga clic en **Quitar marcador**.  
  
3.  Haga clic en el icono de marcador rojo.  
  
4.  Examine el **ubicación de depuración** vuelva a la barra de herramientas. El botón de marcador está atenuado de nuevo. Ha quitado el marcador del único subproceso marcado. Dado que no hay ningún subproceso marcado, la barra de herramientas ha regresado al **mostrar todos los subprocesos** modo. Haga clic en el **subprocesos** lista y compruebe que puede ver todos los subprocesos.  
  
5.  Vuelva a la **subprocesos** ventana y examine las columnas de información.  
  
     En la parte superior de cada columna, la mayoría de los botones tiene títulos que identifican la columna. Sin embargo, la primera columna de la izquierda no tiene ningún título. En su lugar, tiene un icono que es el contorno de un marcador. Observará el mismo contorno en cada fila de la lista de subprocesos. El contorno significa que el subproceso no está marcado.  
  
6.  Haga clic en los contornos de marcador de dos subprocesos: el segundo y el tercero empezando por el final de la lista.  
  
     Los iconos de marcador se vuelven de color rojo sólido, en lugar de mostrarse como contornos huecos.  
  
7.  Haga clic en el botón situado en la parte superior de la columna de marcadores.  
  
     El orden de la lista de subprocesos cambia al hacer clic en el botón. La lista de subprocesos está ordenada ahora con los subprocesos marcados al principio de la misma.  
  
8.  Haga clic otra vez en el botón situado en la parte superior de la columna de marcadores.  
  
     El criterio de ordenación vuelve a cambiar.  
  
## <a name="more-about-the-threads-window"></a>Más información sobre la ventana Subprocesos  
  
#### <a name="to-learn-more-about-the-threads-window"></a>Para obtener más información sobre la ventana Subprocesos  
  
1.  En el **subprocesos** ventana, examine la tercera columna de la izquierda. El botón en la parte superior de esta columna indica **ID**.  
  
2.  Haga clic en **ID**.  
  
     La lista de subprocesos estará ordenada ahora por el número de identificación.  
  
3.  Haga clic con el botón secundario en cualquier subproceso de la lista. En el menú contextual, haga clic en **presentación Hexadecimal**.  
  
     Cambiará el formato del número de id. de subproceso.  
  
4.  Desplace el puntero swl mouse sobre cualquier subproceso de la lista.  
  
     Después de un retraso momentáneo, aparece una información sobre datos. Muestra una pila de llamadas parcial para el subproceso.  
  
5.  Examine la cuarta columna de la izquierda, que tiene la etiqueta **categoría**. Los subprocesos están clasificados en categorías.  
  
     El primer subproceso creado en un proceso se conoce como subproceso principal. Búsquelo en la lista de subprocesos.  
  
6.  Haga clic en el subproceso principal y, a continuación, haga clic en **cambiar a subproceso**.  
  
     Aparecerá un cuadro de diálogo de advertencia. Indica que [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] no puede mostrar el código fuente del subproceso principal.  
  
     Haga clic en **Aceptar**.  
  
7.  Examine el **pila de llamadas** ventana y la **ubicación de depuración** barra de herramientas.  
  
     El contenido de la **pila de llamadas** ventana han cambiado.  
  
## <a name="switching-the-active-thread"></a>Cambiar el subproceso activo  
  
#### <a name="to-switch-threads"></a>Para cambiar subprocesos  
  
1.  En el **subprocesos** ventana, examine la segunda columna de la izquierda. El botón situado en la parte superior de esta columna no tiene ningún texto o icono. Esta columna es el **subproceso activo** columna.  
  
2.  Examine el **subproceso activo** columna y observa que un subproceso tiene una flecha amarilla. Se trata de la *indicador de subproceso activo*.  
  
3.  Tome nota del número de id. de subproceso donde se encuentra el indicador de subproceso activo. Mueva el indicador de subproceso activo a otro subproceso, pero tendrá que volverlo a colocar en su lugar original al finalizar.  
  
4.  Haga clic en otro subproceso y, a continuación, haga clic en **cambiar a subproceso**.  
  
5.  Examine el **pila de llamadas** ventana en la ventana de código fuente. El contenido ha cambiado.  
  
6.  Examine el **ubicación de depuración** barra de herramientas. El subproceso activo también ha cambiado ahí.  
  
7.  Vaya a la **ubicación de depuración** barra de herramientas. Haga clic en el **subproceso** cuadro y elija un subproceso diferente en la lista desplegable.  
  
8.  Examine el **subprocesos** ventana. El indicador de subproceso activo ha cambiado.  
  
9. En la ventana de código fuente, haga clic con el botón secundario en el marcador de un subproceso. En el menú contextual, elija **cambie a** y haga clic en un número de identificador/nombre de subproceso.  
  
     Ahora ha visto tres maneras de cambiar el subproceso activo: utilizando el **subprocesos** ventana, el **subproceso** cuadro el **ubicación de depuración** barra de herramientas y el indicador de subproceso en el ventana de código fuente.  
  
     Con el indicador de subproceso, sólo puede cambiar a subprocesos que se detienen en esa ubicación concreta. Mediante el uso de la **subprocesos** ventana y **ubicación de depuración** barra de herramientas, puede cambiar a cualquier subproceso.  
  
## <a name="freezing-and-thawing-thread-execution"></a>Inmovilizar y reanudar ejecuciones de subprocesos  
  
#### <a name="to-freeze-and-unfreeze-threads"></a>Para inmovilizar y descongelar subprocesos  
  
1.  En el **subprocesos** ventana, haga clic en cualquier subproceso y, a continuación, haga clic en **inmovilizar**.  
  
2.  Observe la columna de subproceso activo. El par de barras verticales aparece ahora ahí. Esas dos barras azules indican que el subproceso está inmovilizado.  
  
3.  Examine el **Suspend** columna. El recuento de suspensión del subproceso ahora es 1.  
  
4.  Haga clic en el subproceso inmovilizado y, a continuación, haga clic en **reanudar**.  
  
     La columna de subproceso activo y el **Suspend** cambio de columna.  
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Cómo: Cambiar a otro subproceso durante la depuración](../debugger/how-to-switch-to-another-thread-while-debugging.md)



