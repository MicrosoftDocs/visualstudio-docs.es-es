---
title: "Tutorial: Depurar una aplicaci&#243;n multiproceso | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depuración multiproceso, tutorial"
  - "tutoriales, depuración multiproceso"
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
caps.latest.revision: 38
caps.handback.revision: 38
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Tutorial: Depurar una aplicaci&#243;n multiproceso
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] proporciona una ventana **Subprocesos** mejorada y otras mejoras de la interfaz de usuario para facilitar la depuración de aplicaciones multiproceso.  Este tutorial dura sólo unos minutos, pero al completarlo, se familiarizará con las nuevas características de la interfaz para depurar aplicaciones multiproceso.  
  
 Para comenzar el tutorial necesita un proyecto de aplicación multiproceso.  Siga los pasos que se enumeran a continuación para crear dicho proyecto.  
  
#### Para crear el proyecto para el tutorial  
  
1.  En el menú **Archivo**, elija **Nuevo** y, a continuación, haga clic en **Proyecto**.  
  
     Aparecerá el cuadro de diálogo **Nuevo proyecto**.  
  
2.  En el cuadro **Tipo de proyecto**, haga clic en el lenguaje que desee: **Visual Basic**, **Visual C\#** o **Visual C\+\+**.  
  
3.  En el cuadro **Plantillas**, elija **Aplicación de consola** o **Aplicación de consola CLR**.  
  
4.  En el cuadro **Nombre**, escriba el nombre MyThreadWalkthroughApp.  
  
5.  Haga clic en **Aceptar**.  
  
     Aparecerá un nuevo proyecto de consola.  Una vez creado el proyecto, aparecerá un archivo de código fuente.  Dependiendo del lenguaje elegido, el archivo de código fuente podría denominarse Module1.vb, Program.cs o MyThreadWalkthroughApp.cpp.  
  
6.  Elimine el código que aparece en el archivo de código fuente y sustitúyalo por el código de ejemplo que aparece en la sección "Crear un subproceso" del tema [Creating Threads and Passing Data at Start Time](../Topic/Creating%20Threads%20and%20Passing%20Data%20at%20Start%20Time.md).  
  
7.  En el menú **Archivo**, haga clic en **Guardar todo**.  
  
#### Para comenzar el tutorial  
  
-   En la ventana de código fuente, busque el código siguiente:  
  
    ```vb  
    Thread.Sleep(3000)   
    Console.WriteLine(  
    ```  
  
```c#  
Thread.Sleep(3000);  
Console.WriteLine();  
```  
  
```cpp  
Thread::Sleep(3000);  
Console.WriteLine();  
```  
  
#### Para iniciar la depuración  
  
1.  Haga clic con el botón secundario en la instrucción `Console.WriteLine`, elija **Punto de interrupción** y, a continuación, haga clic en **Insertar punto de interrupción**.  
  
     En el margen interno izquierdo de la ventana de código fuente, aparecerá una círculo rojo.  Esto indica que ahora hay un punto de interrupción en esa ubicación.  
  
2.  En el menú **Depurar**, haga clic en **Iniciar depuración**.  
  
     La depuración comenzará, la aplicación de consola empezará a ejecutarse y se detendrá en el punto de interrupción.  
  
3.  Si la ventana de la aplicación de consola tiene el foco en ese punto, haga clic en la ventana de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para que el foco vuelva a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  En la ventana de código fuente, busque la línea que contiene el código siguiente:  
  
    ```vb  
    Thread.Sleep(5000)   
    ```  
  
```c#  
Thread.Sleep(3000);  
```  
  
```cpp  
Thread::Sleep(3000);  
```  
  
#### Para detectar el marcador de subproceso  
  
1.  Haga clic con el botón secundario en la ventana **Subprocesos** y, a continuación, haga clic en **Mostrar subprocesos en código fuente**.  
  
2.  Examine el margen interno izquierdo de la ventana.  En esa línea, verá un icono que se asemeja a dos hilos.  Uno es rojo y el otro azul.  El marcador de subproceso indica que un subproceso se ha detenido en esa ubicación.  Posiblemente, el subproceso estará detenido en esa ubicación.  
  
3.  Desplace el puntero sobre el marcador de subproceso.  Aparece una información sobre datos.  En ella se indican el nombre y el número de id. de subproceso de cada subproceso detenido.  En este caso, sólo hay un subproceso, cuyo nombre probablemente es `<noname>`.  
  
4.  Haga clic con el botón secundario en el marcador de subproceso.  Fíjese en las opciones del menú contextual.  
  
 Este icono es un *marcador de subproceso*:  
  
 ![Marcador de subproceso](../debugger/media/threadmarker.png "ThreadMarker")  
  
## Marcar y quitar marcadores de subprocesos  
 En [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)], puede marcar los subprocesos a los que desee prestar una especial atención.  La acción de marcar subprocesos es una buena forma de hacer un seguimiento de los subprocesos importantes y obviar los que no interesen.  
  
#### Para marcar subprocesos  
  
1.  En el menú **Ver**, elija **Barras de herramientas**.  
  
     Asegúrese de que la barra de herramientas **Ubicación de depuración** está seleccionada.  
  
2.  Vaya a la barra de herramientas **Ubicación de depuración** y haga clic en la lista **Subproceso**.  
  
    > [!NOTE]
    >  Puede reconocer esta barra de herramientas mediante tres listas destacadas: **Proceso**, **Subproceso** y **Marco de pila**.  
  
3.  Observe cuántos subprocesos aparecen en la lista.  
  
4.  Regrese a la ventana de código fuente y vuelva a hacer clic con el botón secundario en el marcador **Subproceso**.  
  
5.  En el menú contextual, elija **Marcar** y, a continuación, haga clic en el nombre y número de id. de subproceso.  
  
6.  Regrese a la barra de herramientas **Ubicación de depuración** y vuelva a hacer clic en la lista **Subproceso**.  
  
     Sólo el subproceso marcado aparece ahora en la lista.  El botón de marcador situado inmediatamente a la derecha de la lista **Subproceso**.  El icono de marcador en el botón aparecía antes atenuado.  Ahora se muestra en color rojo brillante sólido.  
  
7.  Desplace el puntero sobre el icono de marcador.  
  
     Aparecerá un elemento emergente.  Este elemento indica cuál es el modo de la lista **Subproceso**: **Mostrar sólo subprocesos marcados**.  
  
8.  Haga clic en el botón de marcador para regresar al modo **Mostrar todos los subprocesos**.  
  
9. Vuelva a hacer clic en la lista **Subproceso** y compruebe que puede ver todos los subprocesos de nuevo.  
  
10. Haga clic en el botón de marcador para regresar a **Mostrar sólo subprocesos marcados**.  
  
11. En el menú **Depurar**, elija **Ventanas** y, a continuación, haga clic en **Subprocesos**.  
  
     Aparecerá la ventana **Subprocesos**.  Un subproceso tendrá asociado un icono de marcador destacado.  
  
12. En la ventana de código fuente, vuelva a hacer clic con el botón secundario en el marcador de subproceso.  
  
     Fíjese en las opciones que ahora están disponibles en el menú contextual.  En lugar de **Marcar**, verá ahora **Quitar marcador**.  No haga clic en **Quitar marcador**.  
  
13. Vaya al siguiente procedimiento sobre cómo quitar marcadores de subprocesos.  
  
#### Para quitar marcadores de subprocesos  
  
1.  En la ventana **Subprocesos**, haga clic con el botón secundario en la línea que corresponde al subproceso marcado.  
  
     Se mostrará un menú contextual.  Tiene las opciones **Quitar marcador** y **Quitar marcador de todos los subprocesos**.  
  
2.  Para quitar el marcador del subproceso, haga clic en **Quitar marcador**.  
  
3.  Haga clic en el icono de marcador rojo.  
  
4.  Vuelva a observar la barra de herramientas **Ubicación de depuración**.  El botón de marcador está atenuado de nuevo.  Ha quitado el marcador del único subproceso marcado.  Dado que no hay ningún subproceso marcado, la barra de herramientas ha regresado al modo **Mostrar todos los subprocesos**.  Haga clic en la lista **Subproceso** y compruebe que puede ver todos los subprocesos.  
  
5.  Regrese a la ventana **Subprocesos** y examine las columnas de información.  
  
     En la parte superior de cada columna, la mayoría de los botones tiene títulos que identifican la columna.  Sin embargo, la primera columna de la izquierda no tiene ningún título.  En su lugar, tiene un icono que es el contorno de un marcador.  Observará el mismo contorno en cada fila de la lista de subprocesos.  El contorno significa que el subproceso no está marcado.  
  
6.  Haga clic en los contornos de marcador de dos subprocesos: el segundo y el tercero empezando por el final de la lista.  
  
     Los iconos de marcador se vuelven de color rojo sólido, en lugar de mostrarse como contornos huecos.  
  
7.  Haga clic en el botón situado en la parte superior de la columna de marcadores.  
  
     El orden de la lista de subprocesos cambia al hacer clic en el botón.  La lista de subprocesos está ordenada ahora con los subprocesos marcados al principio de la misma.  
  
8.  Haga clic otra vez en el botón situado en la parte superior de la columna de marcadores.  
  
     El criterio de ordenación vuelve a cambiar.  
  
## Más información sobre la ventana Subprocesos  
  
#### Para obtener más información sobre la ventana Subprocesos  
  
1.  En la ventana **Subprocesos**, examine la tercera columna de la izquierda.  En el botón de la parte superior de esta columna se lee **Id.**.  
  
2.  Haga clic en **Id.**.  
  
     La lista de subprocesos estará ordenada ahora por el número de identificación.  
  
3.  Haga clic con el botón secundario en cualquier subproceso de la lista.  En el menú contextual, haga clic en **Presentación hexadecimal**.  
  
     Cambiará el formato del número de id. de subproceso.  
  
4.  Desplace el puntero swl mouse sobre cualquier subproceso de la lista.  
  
     Después de un retraso momentáneo, aparece una información sobre datos.  Muestra una pila de llamadas parcial para el subproceso.  
  
5.  Examine la cuarta columna de la izquierda, que se denomina **Categoría**.  Los subprocesos están clasificados en categorías.  
  
     El primer subproceso creado en un proceso se conoce como subproceso principal.  Búsquelo en la lista de subprocesos.  
  
6.  Haga clic con el botón secundario en el subproceso principal y, a continuación, haga clic en **Cambiar a subproceso**.  
  
     Aparecerá un cuadro de diálogo de advertencia.  Indica que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no puede mostrar el código fuente del subproceso principal.  
  
     Haga clic en **Aceptar**.  
  
7.  Examine la ventana **Pila de llamadas** y la barra de herramientas **Ubicación de depuración**.  
  
     El contenido de la ventana **Pila de llamadas** ha cambiado.  
  
## Cambiar el subproceso activo  
  
#### Para cambiar subprocesos  
  
1.  En la ventana **Subprocesos**, examine la segunda columna de la izquierda.  El botón situado en la parte superior de esta columna no tiene ningún texto o icono.  Se trata de la columna **Subproceso activo**.  
  
2.  Examine la columna **Subproceso activo** y observe que un subproceso tiene una flecha amarilla.  Este es el *indicador de subproceso activo*.  
  
3.  Tome nota del número de id. de subproceso donde se encuentra el indicador de subproceso activo.  Mueva el indicador de subproceso activo a otro subproceso, pero tendrá que volverlo a colocar en su lugar original al finalizar.  
  
4.  Haga clic con el botón secundario en otro subproceso y, a continuación, haga clic en **Cambiar a subproceso**.  
  
5.  Examine la ventana **Pila de llamadas** en la ventana de código fuente.  El contenido ha cambiado.  
  
6.  Examine la barra de herramientas **Ubicación de depuración**.  El subproceso activo también ha cambiado ahí.  
  
7.  Vaya a la barra de herramientas **Ubicación de depuración**.  Haga clic en el cuadro **Subproceso** y elija otro subproceso en la lista desplegable.  
  
8.  Examine la ventana **Subprocesos**.  El indicador de subproceso activo ha cambiado.  
  
9. En la ventana de código fuente, haga clic con el botón secundario en el marcador de un subproceso.  En el menú contextual, elija **Cambiar a**y, a continuación, haga clic en un nombre o número de id. de subproceso.  
  
     Ya ha visto tres maneras de cambiar el subproceso activo: utilizando la ventana **Subprocesos**, el cuadro **Subproceso** en la barra de herramientas **Ubicación de depuración**, y el indicador de subproceso en la ventana de código fuente.  
  
     Con el indicador de subproceso, sólo puede cambiar a subprocesos que se detienen en esa ubicación concreta.  Utilizando la ventana **Subprocesos** y la barra de herramientas **Ubicación de depuración**, puede cambiar a cualquier subproceso.  
  
## Inmovilizar y reanudar ejecuciones de subprocesos  
  
#### Para inmovilizar y descongelar subprocesos  
  
1.  En la ventana **Subprocesos**, haga clic con el botón secundario en cualquier subproceso y, a continuación, haga clic en **Inmovilizar**.  
  
2.  Observe la columna de subproceso activo.  El par de barras verticales aparece ahora ahí.  Esas dos barras azules indican que el subproceso está inmovilizado.  
  
3.  Observe la columna **Suspender**.  El recuento de suspensión del subproceso ahora es 1.  
  
4.  Haga clic con el botón secundario en el subproceso inmovilizado y, a continuación, haga clic en **Reanudar**.  
  
     La columna de subproceso activo y la columna **Suspender** cambian.  
  
## Vea también  
 [Depurar aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Cómo: Cambiar a otro subproceso durante la depuración](../debugger/how-to-switch-to-another-thread-while-debugging.md)