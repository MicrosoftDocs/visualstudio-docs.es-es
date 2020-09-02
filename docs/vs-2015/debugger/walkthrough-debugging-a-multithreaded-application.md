---
title: 'Tutorial: depurar una aplicación multiproceso | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 33ce391523a256bcb195deccf0c14868b5eae707
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683094"
---
# <a name="walkthrough-debugging-a-multithreaded-application"></a>Tutorial: Depurar una aplicación multiproceso
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] proporciona una ventana **subprocesos** mejorada y otras mejoras de la interfaz de usuario para facilitar la depuración de aplicaciones multiproceso. Este tutorial dura sólo unos minutos, pero al completarlo, se familiarizará con las nuevas características de la interfaz para depurar aplicaciones multiproceso.  
  
 Para comenzar el tutorial necesita un proyecto de aplicación multiproceso. Siga los pasos que se enumeran a continuación para crear dicho proyecto.  
  
#### <a name="to-create-the-walkthrough-project"></a>Para crear el proyecto para el tutorial  
  
1. En el menú **archivo** , elija **nuevo** y, a continuación, haga clic en **proyecto**.  
  
     Aparecerá el cuadro de diálogo **Nuevo proyecto** .  
  
2. En el cuadro **tipo de proyecto**, haga clic en el lenguaje que prefiera: **Visual Basic**, **Visual C#** o **Visual C++**.  
  
3. En el cuadro **plantillas** , elija **aplicación de consola** o aplicación de **consola CLR**.  
  
4. En el cuadro **nombre** , escriba el nombre MyThreadWalkthroughApp.  
  
5. Haga clic en **Aceptar**.  
  
     Aparecerá un nuevo proyecto de consola. Una vez creado el proyecto, aparecerá un archivo de código fuente. Dependiendo del lenguaje elegido, el archivo de código fuente podría denominarse Module1.vb, Program.cs o MyThreadWalkthroughApp.cpp.  
  
6. Elimine el código que aparece en el archivo de código fuente y reemplácelo por el código de ejemplo que aparece en la sección "crear un subproceso" del tema [crear subprocesos y pasar datos a la hora de inicio](https://msdn.microsoft.com/library/52b32222-e185-4f42-91a7-eaca65c0ab6d).  
  
7. En el menú **Archivo** , haga clic en **Guardar todo**.  
  
#### <a name="to-begin-the-walkthrough"></a>Para comenzar el tutorial  
  
- En la ventana de código fuente, busque el código siguiente:  
  
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
  
1. Haga clic con el botón secundario en la `Console.WriteLine` instrucción, seleccione punto de **interrupción** y haga clic en **Insertar punto de interrupción**.  
  
     En el margen interno izquierdo de la ventana de código fuente, aparecerá una círculo rojo. Esto indica que ahora hay un punto de interrupción en esa ubicación.  
  
2. En el menú **Depurar** , haga clic en **Iniciar depuración**.  
  
     La depuración comenzará, la aplicación de consola empezará a ejecutarse y se detendrá en el punto de interrupción.  
  
3. Si la ventana de la aplicación de consola tiene el foco en ese punto, haga clic en la ventana de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para que el foco vuelva a [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4. En la ventana de código fuente, busque la línea que contiene el código siguiente:  
  
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
  
1. Haga clic con el botón secundario en la ventana **subprocesos** y después haga clic en **Mostrar subprocesos en origen**.  
  
2. Examine el margen interno izquierdo de la ventana. En esa línea, verá un icono que se asemeja a dos hilos. Uno es rojo y el otro azul. El marcador de subproceso indica que un subproceso se ha detenido en esa ubicación. Posiblemente, el subproceso estará detenido en esa ubicación.  
  
3. Desplace el puntero sobre el marcador de subproceso. Aparece una información sobre datos. En ella se indican el nombre y el número de id. de subproceso de cada subproceso detenido. En este caso, sólo hay un subproceso, cuyo nombre probablemente es `<noname>`.  
  
4. Haga clic con el botón secundario en el marcador de subproceso. Fíjese en las opciones del menú contextual.  
  
   Este icono es un *marcador de subproceso*:  
  
   ![Marcador de subproceso](../debugger/media/threadmarker.gif "ThreadMarker")  
  
## <a name="flagging-and-unflagging-threads"></a>Marcar y quitar marcadores de subprocesos  
 En [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)], puede marcar los subprocesos a los que desee prestar una especial atención. La acción de marcar subprocesos es una buena forma de hacer un seguimiento de los subprocesos importantes y obviar los que no interesen.  
  
#### <a name="to-flag-threads"></a>Para marcar subprocesos  
  
1. En el menú **Ver** , seleccione **barras de herramientas**.  
  
     Asegúrese de que la barra de herramientas **Ubicación de depuración** está seleccionada.  
  
2. Vaya a la barra de herramientas **Ubicación de depuración** y haga clic en la lista **subproceso** .  
  
    > [!NOTE]
    > Puede reconocer esta barra de herramientas por tres listas destacadas: **proceso**, **subproceso**y **marco de pila**.  
  
3. Observe cuántos subprocesos aparecen en la lista.  
  
4. Vuelva a la ventana de código fuente y vuelva a hacer clic con el botón secundario en el marcador de **subproceso** .  
  
5. En el menú contextual, seleccione **marca**y, a continuación, haga clic en el nombre del subproceso y el número de identificación.  
  
6. Vuelva a la barra de herramientas **Ubicación de depuración** y vuelva a hacer clic en la lista de **subprocesos** .  
  
     Sólo el subproceso marcado aparece ahora en la lista. Botón de marca que está justo a la derecha de la lista de **subprocesos** . El icono de marcador en el botón aparecía antes atenuado. Ahora se muestra en color rojo brillante sólido.  
  
7. Desplace el puntero sobre el icono de marcador.  
  
     Aparecerá un elemento emergente. Este elemento emergente indica el modo en que se encuentra la lista de **subprocesos** : **Mostrar solo los subprocesos marcados**.  
  
8. Haga clic en el botón de marca para volver al modo **Mostrar todos los subprocesos** .  
  
9. Vuelva a hacer clic en la lista de **subprocesos** y compruebe que ahora puede ver todos los subprocesos de nuevo.  
  
10. Haga clic en el botón de marca para volver a **Mostrar solo los subprocesos marcados**.  
  
11. En el menú **Depurar**, elija **Ventanas** y, a continuación, haga clic en **Subprocesos**.  
  
     Aparece la ventana **subprocesos** . Un subproceso tendrá asociado un icono de marcador destacado.  
  
12. En la ventana de código fuente, vuelva a hacer clic con el botón secundario en el marcador de subproceso.  
  
     Fíjese en las opciones que ahora están disponibles en el menú contextual. En lugar de la **marca**, ahora verá **Unflag**. No haga clic en **Quitar marcador**.  
  
13. Vaya al siguiente procedimiento sobre cómo quitar marcadores de subprocesos.  
  
#### <a name="to-unflag-threads"></a>Para quitar marcadores de subprocesos  
  
1. En la ventana **subprocesos** , haga clic con el botón secundario en la línea correspondiente al subproceso marcado.  
  
     Se mostrará un menú contextual. Tiene opciones para quitar la **marca** y **quitar la marca de todos**.  
  
2. Para quitar la marca del subproceso, haga clic en **Quitar marcador**.  
  
3. Haga clic en el icono de marcador rojo.  
  
4. Vuelva a mirar la barra de herramientas **Ubicación de depuración** . El botón de marcador está atenuado de nuevo. Ha quitado el marcador del único subproceso marcado. Dado que no hay ningún subproceso marcado, la barra de herramientas ha regresado al modo **Mostrar todos los subprocesos** . Haga clic en la lista **subproceso** y compruebe que puede ver todos los subprocesos.  
  
5. Vuelva a la ventana **subprocesos** y examine las columnas de información.  
  
     En la parte superior de cada columna, la mayoría de los botones tiene títulos que identifican la columna. Sin embargo, la primera columna de la izquierda no tiene ningún título. En su lugar, tiene un icono que es el contorno de un marcador. Observará el mismo contorno en cada fila de la lista de subprocesos. El contorno significa que el subproceso no está marcado.  
  
6. Haga clic en los contornos de marcador de dos subprocesos: el segundo y el tercero empezando por el final de la lista.  
  
     Los iconos de marcador se vuelven de color rojo sólido, en lugar de mostrarse como contornos huecos.  
  
7. Haga clic en el botón situado en la parte superior de la columna de marcadores.  
  
     El orden de la lista de subprocesos cambia al hacer clic en el botón. La lista de subprocesos está ordenada ahora con los subprocesos marcados al principio de la misma.  
  
8. Haga clic otra vez en el botón situado en la parte superior de la columna de marcadores.  
  
     El criterio de ordenación vuelve a cambiar.  
  
## <a name="more-about-the-threads-window"></a>Más información sobre la ventana Subprocesos  
  
#### <a name="to-learn-more-about-the-threads-window"></a>Para obtener más información sobre la ventana Subprocesos  
  
1. En la ventana **subprocesos** , examine la tercera columna de la izquierda. El botón situado en la parte superior de esta columna indica **ID**.  
  
2. Haga clic en **ID**.  
  
     La lista de subprocesos estará ordenada ahora por el número de identificación.  
  
3. Haga clic con el botón secundario en cualquier subproceso de la lista. En el menú contextual, haga clic en **presentación hexadecimal**.  
  
     Cambiará el formato del número de id. de subproceso.  
  
4. Desplace el puntero swl mouse sobre cualquier subproceso de la lista.  
  
     Después de un retraso momentáneo, aparece una información sobre datos. Muestra una pila de llamadas parcial para el subproceso.  
  
5. Fíjese en la cuarta columna de la izquierda, que está etiquetada como **categoría**. Los subprocesos están clasificados en categorías.  
  
     El primer subproceso creado en un proceso se conoce como subproceso principal. Búsquelo en la lista de subprocesos.  
  
6. Haga clic con el botón secundario en el subproceso principal y, a continuación, haga clic en **cambiar a subproceso**.  
  
     Aparece un cuadro de diálogo de advertencia. Indica que [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] no puede mostrar el código fuente del subproceso principal.  
  
     Haga clic en **Aceptar**.  
  
7. Fíjese en la ventana **pila de llamadas** y en la barra de herramientas ubicación de **depuración** .  
  
     El contenido de la ventana **pila de llamadas** ha cambiado.  
  
## <a name="switching-the-active-thread"></a>Cambiar el subproceso activo  
  
#### <a name="to-switch-threads"></a>Para cambiar subprocesos  
  
1. En la ventana **subprocesos** , examine la segunda columna de la izquierda. El botón situado en la parte superior de esta columna no tiene ningún texto o icono. Esta columna es la columna de **subproceso activo** .  
  
2. Fíjese en la columna de **subproceso activo** y observe que un subproceso tiene una flecha amarilla. Este es el *indicador de subproceso activo*.  
  
3. Tome nota del número de id. de subproceso donde se encuentra el indicador de subproceso activo. Mueva el indicador de subproceso activo a otro subproceso, pero tendrá que volverlo a colocar en su lugar original al finalizar.  
  
4. Haga clic con el botón secundario en otro subproceso y haga clic en **cambiar a subproceso**.  
  
5. Fíjese en la ventana **pila de llamadas** de la ventana de código fuente. El contenido ha cambiado.  
  
6. Fíjese en la barra de herramientas **Ubicación de depuración** . El subproceso activo también ha cambiado ahí.  
  
7. Vaya a la barra de herramientas **Ubicación de depuración** . Haga clic en el cuadro **subproceso** y elija otro subproceso de la lista desplegable.  
  
8. Fíjese en la ventana **subprocesos** . El indicador de subproceso activo ha cambiado.  
  
9. En la ventana de código fuente, haga clic con el botón secundario en el marcador de un subproceso. En el menú contextual, seleccione **cambiar a** y haga clic en un número de identificador/nombre de subproceso.  
  
     Ahora ha detectado tres maneras de cambiar el subproceso activo: mediante la **ventana subprocesos** , el cuadro **subproceso** de la barra de herramientas **Ubicación de depuración** y el indicador de subproceso en la ventana de código fuente.  
  
     Con el indicador de subproceso, sólo puede cambiar a subprocesos que se detienen en esa ubicación concreta. Utilizando la ventana **Subprocesos** y la barra de herramientas **Ubicación de depuración**, puede cambiar a cualquier subproceso.  
  
## <a name="freezing-and-thawing-thread-execution"></a>Inmovilizar y reanudar ejecuciones de subprocesos  
  
#### <a name="to-freeze-and-unfreeze-threads"></a>Para inmovilizar y descongelar subprocesos  
  
1. En la ventana **subprocesos** , haga clic con el botón secundario en cualquier subproceso y haga clic en **inmovilizar**.  
  
2. Observe la columna de subproceso activo. El par de barras verticales aparece ahora ahí. Esas dos barras azules indican que el subproceso está inmovilizado.  
  
3. Fíjese en la columna **suspender** . El recuento de suspensión del subproceso ahora es 1.  
  
4. Haga clic con el botón secundario en el subproceso inmovilizado y haga clic en **reanudar**.  
  
     La columna de subproceso activo y la columna de **suspensión** cambian.  
  
## <a name="see-also"></a>Consulte también  
 [Depuración de aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Cómo: cambiar a otro subproceso durante la depuración](../debugger/how-to-switch-to-another-thread-while-debugging.md)
