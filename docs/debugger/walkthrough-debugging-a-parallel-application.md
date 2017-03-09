---
title: "Tutorial: Depurar una aplicaci&#243;n paralela | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "depurador, tutorial para tareas paralelas"
  - "depurar, aplicaciones paralelas"
  - "aplicaciones paralelas, depurar [C#]"
  - "aplicaciones paralelas, depurar [C++]"
  - "aplicaciones paralelas, depurar [Visual Basic]"
  - "ventana de herramientas Pilas paralelas"
  - "ventana de herramientas Tareas paralelas"
ms.assetid: 2820ac4c-c893-4d87-8c62-83981d561493
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Tutorial: Depurar una aplicaci&#243;n paralela
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este tutorial se muestra cómo utilizar las ventanas **Pilas paralelas** y **Tareas paralelas** para depurar una aplicación paralela.  Estas ventanas ayudan a entender y comprobar el comportamiento en tiempo de ejecución del código que utiliza [Task Parallel Library \(TPL\)](../Topic/Task%20Parallel%20Library%20\(TPL\).md) o [Runtime de simultaneidad](/visual-cpp/parallel/concrt/concurrency-runtime).  En este tutorial se proporciona código de muestra con puntos de interrupción integrados.  Una vez que el código se interrumpe, se muestra cómo utilizar las ventanas **Tareas paralelas** y **Pilas paralelas** para examinarlo.  
  
 Se enseñan estas tareas:  
  
-   Cómo ver las pilas de llamadas de todos los subprocesos en una vista.  
  
-   Cómo ver la lista de instancias de `System.Threading.Tasks.Task` que se crean en la aplicación.  
  
-   Cómo ver las pilas de llamadas reales de las tareas en lugar de los subprocesos.  
  
-   Cómo navegar al código desde las ventanas **Tareas paralelas** y **Pilas paralelas**.  
  
-   Cómo trabajan las ventanas con la escala de tamaño mediante la agrupación, el zoom y otras características relacionadas.  
  
## Requisitos previos  
 En el tutorial se supone que **Solo mi código** está habilitado.  En el menú **Herramientas**, haga clic en **Opciones**, expanda el nodo **Depuración**, seleccione **General** y, a continuación, seleccione **Habilitar Solo mi código \(solo administrado\)**.  Si no configura esta característica, puede utilizar este tutorial, pero los resultados pueden diferir de las ilustraciones.  
  
## Ejemplo de C\#  
 Si utiliza el ejemplo de C\#, también se supone que Código externo está oculto.  Para alternar si se muestra el código externo, haga clic con el botón secundario en el encabezado de tabla **Nombre** de la ventana **Pila de llamadas** y, a continuación, active o desactive **Mostrar código externo**.  Si no configura esta característica, puede utilizar este tutorial, pero los resultados pueden diferir de las ilustraciones.  
  
## Ejemplo de C\+\+  
 Si utiliza el ejemplo C\+\+, puede omitir las referencias a Código externo de este tema.  El código externo solo se aplica en el ejemplo de C\#.  
  
## Ilustraciones  
 Las ilustraciones de este tema se grabaron en un equipo básico quad core que ejecuta el ejemplo de C\#.  Aunque puede utilizar otras configuraciones para completar este tutorial, las ilustraciones pueden diferir de lo que se muestra en su equipo.  
  
## Crear el proyecto de muestra  
 El código de ejemplo de este tutorial es para una aplicación que no hace nada.  El objetivo es entender cómo utilizar las ventanas de herramientas para depurar una aplicación paralela.  
  
#### Para crear el proyecto de ejemplo  
  
1.  En el menú **Archivo** de Visual Studio, elija **Nuevo** y, a continuación, haga clic en **Proyecto**.  
  
2.  En el panel **Plantillas instaladas**, seleccione Visual C\#, Visual Basic o Visual C\+\+.  En los lenguajes administrados, asegúrese de que aparece [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] en el cuadro del marco.  
  
3.  Seleccione **Aplicación de consola** y, a continuación, haga clic en **Aceptar**.  Mantenga la configuración Debug, que es el valor predeterminado.  
  
4.  Abra el archivo de código .cpp, .cs o .vb del proyecto.  Elimine su contenido para crear un archivo de código vacío.  
  
5.  En el archivo de código vacío, pegue el siguiente código en el lenguaje elegido.  
  
 [!code-cs[Debugger#1](../debugger/codesnippet/CSharp/walkthrough-debugging-a-parallel-application_1.cs)]
 [!code-cpp[Debugger#1](../debugger/codesnippet/CPP/walkthrough-debugging-a-parallel-application_1.cpp)]
 [!code-vb[Debugger#1](../debugger/codesnippet/VisualBasic/walkthrough-debugging-a-parallel-application_1.vb)]  
  
1.  En el menú **Archivo**, haga clic en **Guardar todo**.  
  
2.  En el menú **Compilar**, haga clic en **Recompilar solución**.  
  
     Observe que hay cuatro llamadas a `Debugger.Break` \(`DebugBreak` en el ejemplo de C\+\+\). Por tanto, no tiene que insertar puntos de interrupción; simplemente ejecutando la aplicación, el depurador se interrumpirá cuatro veces.  
  
## Utilizar la ventana Pilas paralelas: vista de subprocesos  
 En el menú **Depurar**, haga clic en **Iniciar depuración**.  Espere a que se alcance el primer punto de interrupción.  
  
#### Para ver la pila de llamadas de un subproceso  
  
1.  En el menú **Depurar**, elija **Ventanas** y, a continuación, haga clic en **Subprocesos**.  Acople la ventana **Subprocesos** en la parte inferior de Visual Studio.  
  
2.  En el menú **Depurar**, seleccione **Ventanas** y, a continuación, haga clic en **Pila de llamadas**.  Acople la ventana **Pila de llamadas** en la parte inferior de Visual Studio.  
  
3.  Haga doble clic en un subproceso en la ventana **Subprocesos** para que sea el actual.  Los subprocesos actuales tienen una flecha amarilla.  Al cambiar el subproceso actual, la pila de llamadas se muestra en la ventana **Pila de llamadas**.  
  
#### Para examinar la ventana Pilas paralelas  
  
1.  En el menú **Depurar**, seleccione **Ventanas** y, a continuación, haga clic en **Pilas paralelas**.  Asegúrese de que **Subprocesos** está seleccionado en el cuadro de la esquina superior izquierda.  
  
     Utilizando la ventana **Pilas paralelas**, puede ver al mismo tiempo varias pilas de llamadas en una vista.  La siguiente ilustración muestra la ventana **Pilas paralelas** sobre la ventana **Pila de llamadas**.  
  
     ![Vista Subprocesos en la ventana Pilas paralelas](../debugger/media/pdb_walkthrough_1.png "PDB\_Walkthrough\_1")  
  
     La pila de llamadas del subproceso principal aparece en un cuadro y las pilas de llamadas de los otros cuatro subprocesos están agrupadas en otro cuadro.  Se agrupan cuatro subprocesos porque sus marcos de pila comparten los mismos contextos de método, es decir, están en los mismos métodos: `A`, `B` y `C`.  Para ver los identificadores y los nombres de los subprocesos que comparten el mismo cuadro, desplace el puntero del mouse sobre el encabezado \(**4 Subprocesos**\).  El subproceso actual se muestra en negrita, como en la siguiente ilustración.  
  
     ![Información sobre herramientas con identificadores y nombres de subprocesos](../debugger/media/pdb_walkthrough_1a.png "PDB\_Walkthrough\_1A")  
  
     La flecha amarilla indica el marco de pila activo del subproceso actual.  Para obtener más información, desplace el puntero del mouse sobre él  
  
     ![Información sobre herramientas en marco de pila activo](../debugger/media/pdb_walkthrough_1b.png "PDB\_Walkthrough\_1B")  
  
     Puede establecer cuánto detalle mostrar en los marcos de pila \(**Nombres del módulo**, **Tipos de parámetros**, **Nombres de parámetros**, **Valores de parámetro**, **Números de línea** y **Desplazamientos de bytes**\) haciendo clic con el botón secundario del mouse en la ventana **Pila de llamadas**.  
  
     Un resaltado azul alrededor de un cuadro indica que el subproceso actual forma parte de ese cuadro.  El subproceso actual también está indicado por el marco de pila en negrita de la información sobre herramientas.  Si hace doble clic en el subproceso principal en la ventana Subprocesos, puede observar que el resaltado azul de la ventana **Pilas paralelas** se mueve de forma acorde.  
  
     ![Subproceso principal resaltado en la ventana Pilas paralelas](../debugger/media/pdb_walkthrough_1c.png "PDB\_Walkthrough\_1C")  
  
#### Para reanudar la ejecución hasta el segundo punto de interrupción  
  
1.  Para reanudar la ejecución hasta llegar al segundo punto de interrupción, haga clic en **Continuar** en el menú **Depurar**.  La siguiente ilustración muestra el árbol de subproceso en el segundo punto de interrupción.  
  
     ![Ventana Pilas paralelas con muchas bifurcaciones](../debugger/media/pdb_walkthrough_2.png "PDB\_Walkthrough\_2")  
  
     En el primer punto de interrupción, cuatro subprocesos fueron de S.A a S.B a los métodos S.C.  Esa información todavía está visible en la ventana **Pilas paralelas**, pero los cuatro subprocesos han progresado más.  Uno de ellos continuó a S.D y a S.E.  Otro continuó hasta S.F, S.G y S.H.  Los otros dos continuaron a S.I y S.J, y de allí uno fue a S.K y el otro continuó a código externo de no usuario.  
  
     Puede desplazar el puntero del mouse sobre el encabezado del cuadro, por ejemplo, **1 subproceso** o **2 subprocesos**, para ver los identificadores de subproceso de los subprocesos.  Puede desplazar el puntero del mouse sobre los marcos de pila para ver identificadores de subproceso y otros detalles del marco.  El resaltado azul indica el subproceso actual y la flecha amarilla indica el marco de pila activo del subproceso actual.  
  
     El icono de los subprocesos \(las líneas onduladas azules y rojas superpuestas\) indica los marcos de pila activos de los subprocesos que no son el actual.  En la ventana **Pila de llamadas**, haga doble clic en S.B para intercambiar los marcos.  La ventana **Pilas paralelas** indica el marco de pila del subproceso actual utilizando un icono de flecha verde y curvada.  
  
     En la ventana **Subprocesos**, intercambie entre los subprocesos y observe que la vista en la ventana **Pilas paralelas** está actualizada.  
  
     Puede cambiar a otro subproceso o al marco de otro subproceso, utilizando el menú contextual en la ventana **Pilas paralelas**.  Por ejemplo, haga clic con el botón secundario en S.J, apunte a **Cambiar a marco** y, a continuación, haga clic en un comando.  
  
     ![Ruta de acceso a pilas paralelas de ejecución](../debugger/media/pdb_walkthrough_2b.png "PDB\_Walkthrough\_2B")  
  
     Haga clic con el botón secundario en S.C y señale a **Cambiar a marco**.  Uno de los comandos tiene una marca de verificación que indica el marco de pila del subproceso actual.  Puede cambiar a ese marco del mismo subproceso \(la flecha verde se moverá\) o puede cambiar al otro subproceso \(el resaltado azul también moverá\).  La ilustración siguiente muestra los submenús.  
  
     ![Menú Pilas con 2 opciones en el marco del subproceso C mientras que el actual es el J](../debugger/media/pdb_walkthrough_3.png "PDB\_Walkthrough\_3")  
  
     Cuando un contexto de método está asociado solo a un marco de pila, el encabezado del cuadro muestra **1 subproceso** y puede cambiar a él haciendo doble clic.  Si hace doble clic en un contexto de método que tiene más que un marco asociado, el menú se abre automáticamente.  Cuando desplace el puntero del mouse sobre los contextos de método, observe el triángulo negro a la derecha.  Al hacer clic en ese triángulo, también se muestra el menú contextual.  
  
     Con aplicaciones grandes que tienen muchos subprocesos, le interesa centrarse en un subconjunto de subprocesos.  La ventana **Pilas paralelas** solo puede mostrar las pilas de llamadas de los subprocesos marcados.  En la barra de herramientas, haga clic en el botón **Mostrar marcadas únicamente** junto al cuadro de lista.  
  
     ![Ventana Pilas paralelas vacía e información sobre herramientas](../debugger/media/pdb_walkthrough_3a.png "PDB\_Walkthrough\_3A")  
  
     A continuación, en la ventana **Subprocesos**, marque los subprocesos uno por uno para ver cómo sus pilas de llamadas aparecen en la ventana **Pilas paralelas**.  Para marcar subprocesos, utilice el menú contextual o la primera celda de un subproceso.  Haga clic de nuevo en el botón de la barra de herramientas **Mostrar marcadas únicamente** para mostrar todos los subprocesos.  
  
#### Para reanudar la ejecución hasta el tercer punto de interrupción  
  
1.  Para reanudar la ejecución hasta llegar al tercer punto de interrupción, haga clic en **Continuar** en el menú **Depurar**.  
  
     Cuando varios subprocesos están en el mismo método pero el método no estaba al principio de la pila de llamadas, el método aparece en cuadros diferentes.  Un ejemplo en el punto de interrupción actual es S.L, que tiene tres subprocesos y aparece en tres cuadros.  Haga doble clic en S.L.  
  
     ![Ruta de acceso de ejecución en la ventana Pilas paralelas](../debugger/media/pdb_walkthrough_3b.png "PDB\_Walkthrough\_3B")  
  
     Observe que S.L está en negrita en los otros dos cuadros para que pueda ver dónde más aparece.  Si desea ver qué marcos llaman a S.L y a qué marcos llama, haga clic en el botón **Alternar vista de método** en la barra de herramientas.  La siguiente ilustración muestra la vista de método de la ventana **Pilas paralelas**.  
  
     ![Vista Método en la ventana Pilas paralelas](../debugger/media/pdw_walkthrough_4.png "PDW\_Walkthrough\_4")  
  
     Observe cómo el diagrama se monta en el método seleccionado y lo coloca en su propio cuadro en el medio de la vista.  Los destinatarios y llamadores aparecen en la parte superior e inferior.  Haga clic de nuevo en el botón **Alternar vista de método** para dejar este modo.  
  
     El menú contextual de la ventana **Pilas paralelas** también tiene los siguientes otros elementos.  
  
    -   **Presentación hexadecimal** alterna los números de la información sobre herramientas entre decimal y hexadecimal.  
  
    -   **Información de carga de símbolos** y **Configuración de símbolos** abren los cuadros de diálogo respectivos.  
  
    -   **Ir al código fuente** e **Ir al desensamblado** navegan en el editor hasta el método seleccionado.  
  
    -   **Mostrar código externo** muestra todos los marcos aun cuando no estén en código de usuario.  Pruébelo para ver el diagrama expandirse para alojar los marcos adicionales \(que pueden estar atenuados porque no tiene símbolos para ellos\).  
  
     Si tiene diagramas grandes y pasa al punto de interrupción siguiente, tal vez le interese la vista para desplazarse de forma automática al marco de pila activo del subproceso actual, es decir, el subproceso que alcanzó primero el punto de interrupción.  En la ventana **Pilas paralelas** asegúrese de que el botón **Desplazar automáticamente a marco de pila actual** de la barra de herramientas está activado.  
  
     ![Desplazamiento automático en la ventana Pilas paralelas](../debugger/media/pdb_walkthrough_4a.png "PDB\_Walkthrough\_4A")  
  
2.  Antes de continuar, en la ventana **Pilas paralelas**, desplácese a la izquierda y hacia abajo todo lo posible.  
  
#### Para reanudar la ejecución hasta el cuarto punto de interrupción  
  
1.  Para reanudar la ejecución hasta llegar al cuarto punto de interrupción, haga clic en **Continuar** en el menú **Depurar**.  
  
     Observe cómo la vista se desplaza automáticamente para ocupar su lugar.  Alterne los subprocesos en la ventana **Subprocesos** o alterne los marcos de pila en la ventana **Pila de llamadas** y observe cómo la vista siempre se desplaza automáticamente hasta el marco correcto.  Desactive la opción **Desplazar automáticamente a marco de pila actual** y vea la diferencia.  
  
     La **Vista aérea** también permite ver diagramas grandes en la ventana **Pilas paralelas**.  Para ver la **Vista aérea**, haga clic en el botón situado entre las barras de desplazamiento en la esquina inferior derecha de la ventana, como se muestra en la siguiente ilustración.  
  
     ![Vista de pájaro en la ventana Pilas paralelas](../debugger/media/pdb_walkthrough_5.png "PDB\_Walkthrough\_5")  
  
     Puede mover el rectángulo para hacer una rápida panorámica del diagrama.  
  
     Otra manera de mover el diagrama en cualquier dirección es haciendo clic en un área en blanco del diagrama y arrastrando al lugar deseado.  
  
     Para acercar y alejar, mantenga presionada la tecla CTRL mientras mueve la rueda del mouse.  Alternativamente, haga clic en el botón Zoom en la barra de herramientas y utilice la herramienta Zoom.  
  
     ![Pilas ampliadas en la ventana Pilas paralelas](../debugger/media/pdb_walkthrough_5a.png "PDB\_Walkthrough\_5A")  
  
     También puede ver las pilas en dirección descendente en lugar de ascendente haciendo clic en el menú **Herramientas**, en **Opciones** y seleccionando o borrando la opción bajo el nodo **Depuración**.  
  
2.  Antes de continuar, en el menú **Depurar**, haga clic en **Detener depuración** para finalizar la ejecución.  
  
## Utilizar la ventana Tareas paralelas y la vista Tareas de la ventana Pilas paralelas  
 Recomendamos completar los procedimientos anteriores antes de continuar.  
  
#### Para reiniciar la aplicación hasta que alcance el primer punto de interrupción  
  
1.  En el menú **Depurar**, haga clic en **Iniciar depuración** y espere hasta alcanzar el primer punto de interrupción.  
  
2.  En el menú **Depurar**, elija **Ventanas** y, a continuación, haga clic en **Subprocesos**.  Acople la ventana **Subprocesos** en la parte inferior de Visual Studio.  
  
3.  En el menú **Depurar**, seleccione **Ventanas** y, a continuación, haga clic en **Pila de llamadas**.  Acople la ventana **Pila de llamadas** en la parte inferior de Visual Studio.  
  
4.  Haga doble clic en un subproceso de la ventana **Subprocesos** para que sea el actual.  Los subprocesos actuales tienen la flecha amarilla.  Al cambiar el subproceso actual, las otras ventanas se actualizan.  A continuación, examinaremos las tareas.  
  
5.  En el menú **Depurar**, apunte a **Ventanas** y, a continuación, haga clic en **Tareas paralelas**.  La siguiente ilustración muestra la ventana **Tareas paralelas**.  
  
     ![Cuatro tareas en ejecución en la ventana Tareas paralelas](../debugger/media/pdw_walkthrough_6.png "PDW\_Walkthrough\_6")  
  
     Por cada tarea que se esté ejecutando, puede leer su identificador, que devuelve la propiedad del mismo nombre, el identificador y nombre del subproceso que lo ejecuta, su ubicación \(desplazando el puntero del mouse para mostrar una información sobre herramientas con la pila de llamadas completa\).  Asimismo, en la columna **Tarea**, puede ver el método que se pasó a la tarea; en otras palabras, el punto inicial.  
  
     Puede ordenar cualquier columna.  Observe el glifo de ordenación que indica la columna y la dirección de ordenación.  También puede reordenar las columnas arrastrándolas a izquierda o derecha.  
  
     La flecha amarilla indica la tarea actual.  Puede intercambiar las tareas haciendo doble clic en una tarea o utilizando el menú contextual.  Al intercambiar las tareas, el subproceso subyacente pasa a ser el actual y las demás ventanas se actualizan.  
  
     Cuando pasa manualmente de una tarea a otra, la flecha amarilla se mueve, pero una flecha blanca sigue mostrando la tarea que hizo que el depurador se interrumpiera.  
  
#### Para reanudar la ejecución hasta el segundo punto de interrupción  
  
1.  Para reanudar la ejecución hasta llegar al segundo punto de interrupción, haga clic en **Continuar** en el menú **Depurar**.  
  
     Previamente, la columna **Estado** mostraba todas las tareas como en ejecución, pero ahora dos de las tareas están en espera.  Las tareas se pueden bloquear por muchas razones diferentes.  En la columna **Estado**, desplace el puntero del mouse sobre una tarea en espera para saber por qué está bloqueada.  Por ejemplo, en la siguiente ilustración, la tarea 3 está esperando a la tarea 4.  
  
     ![Dos tareas en espera en la ventana Tareas paralelas](../debugger/media/pdb_walkthrough_7.png "PDB\_Walkthrough\_7")  
  
     La tarea 4, a su vez, está esperando a un monitor que pertenece al subproceso asignado a la tarea 2.  
  
     ![Tarea en espera e información sobre herramientas en la ventana Tareas](../debugger/media/pdb_walkthrough_7a.png "PDB\_Walkthrough\_7A")  
  
     Puede marcar una tarea haciendo clic en la marca en la primera columna de la ventana **Tareas paralelas**.  
  
     Puede utilizar las marcas para realizar el seguimiento de las tareas entre los puntos de interrupción diferentes en la misma sesión de depuración o filtrar por las tareas cuyas pilas de llamadas se muestren en la ventana **Pilas paralelas**.  
  
     Cuando utilizó la ventana **Pilas paralelas** anteriormente, vio los subprocesos de la aplicación.  Mire la ventana **Pilas paralelas** de nuevo, pero esta vez observe las tareas de la aplicación.  Haga esto seleccionando **Tareas** en el cuadro de la izquierda superior.  En la siguiente ilustración se muestra la vista Tareas.  
  
     ![Vista Subprocesos en la ventana Pilas paralelas](../debugger/media/pdb_walkthrough_8.png "PDB\_Walkthrough\_8")  
  
     Los subprocesos que no están ejecutando tareas actualmente no se muestran en el vista de tareas de la ventana **Pilas paralelas**.  Asimismo, con los subprocesos que ejecutan tareas, algunos de los marcos de pila que no son pertinentes para las tareas se filtran de la parte superior e inferior de la pila.  
  
     Observe la ventana **Tareas paralelas** de nuevo.  Haga clic con el botón secundario en cualquier encabezado de columna para ver un menú contextual de la columna.  
  
     ![Menú de vista contextual en la ventana Pilas paralelas](../debugger/media/pdb_walkthrough_8a.png "PDB\_Walkthrough\_8A")  
  
     Puede utilizar el menú contextual para agregar o quitar las columnas.  Por ejemplo, la columna AppDomain no está seleccionada; por consiguiente, no se muestra en la lista.  Haga clic en **Primario**.  La columna **Primario** aparece sin valores para las cuatro tareas.  
  
#### Para reanudar la ejecución hasta el tercer punto de interrupción  
  
1.  Para reanudar la ejecución hasta llegar al tercer punto de interrupción, haga clic en **Continuar** en el menú **Depurar**.  
  
     Ahora se está ejecutando una nueva tarea, la tarea 5, y la tarea 4 está en espera.  Puede ver por qué desplazando el puntero del mouse sobre la tarea en espera de la ventana **Estado**.  En la columna **Primario**, observe que tarea 4 es el elemento primario de la tarea 5.  
  
     Para visualizar la relación primario\-secundario mejor, haga clic con el botón secundario en el encabezado de columna **Primario** y, a continuación, haga clic en **Vista de elemento primario y secundario**.  Vea la ilustración siguiente:  
  
     ![Vista de elemento primario y secundario en la ventana Tareas paralelas](../debugger/media/pdb_walkthrough_9.png "PDB\_Walkthrough\_9")  
  
     Observe que la tarea 4 y 5 se están ejecutando en el mismo subproceso.  Esta información no se muestra en la ventana **Subprocesos**; poder verlo aquí es otra de las ventajas de la ventana **Tareas paralelas**.  Para confirmar esto, vea la ventana **Pilas paralelas**.  Asegúrese de que está viendo **Tareas**.  Busque las tareas 4 y 5 haciendo doble clic en ellas en la ventana **Tareas paralelas**.  Al hacerlo, se actualiza el resaltado azul de la ventana **Pilas paralelas**.  También puede buscar las tareas 4 y 5 examinando la información sobre herramientas en la ventana **Pilas paralelas**.  
  
     ![Vista Tarea en la ventana Pilas paralelas](../debugger/media/pdb_walkthrough_9a.png "PDB\_Walkthrough\_9A")  
  
     En la ventana **Pilas paralelas**, haga clic con el botón secundario en S.P y, a continuación, haga clic en **Ir al subproceso**.  La ventana cambia a la vista de subprocesos y el marco correspondiente está a la vista.  Puede ver ambas tareas en el mismo subproceso.  
  
     ![Subproceso resaltado en la vista de subprocesos](../debugger/media/pdb_walkthrough_9b.png "PDB\_Walkthrough\_9B")  
  
     Esta es otra ventaja de la vista de tareas de la ventana **Pilas paralelas**, comparada con la ventana **Subprocesos**.  
  
#### Para reanudar la ejecución hasta el cuarto punto de interrupción  
  
1.  Para reanudar la ejecución hasta llegar al tercer punto de interrupción, haga clic en **Continuar** en el menú **Depurar**.  Haga clic en el encabezado de columna **Id.** para ordenar por identificador.  Vea la ilustración siguiente:  
  
     ![Cuatro estados de tarea en la ventana Pilas paralelas](../debugger/media/pdb_walkthrough_10.png "PDB\_Walkthrough\_10")  
  
     Como la tarea 5 se ha completado, ya no se muestra.  Si no es el caso en su equipo y no se muestra el interbloqueo, avance un paso presionando F11.  
  
     Las tareas 3 y 4 se están esperando mutuamente y están interbloqueadas.  Hay también 5 nuevas tareas que son elementos secundarios de la tarea 2 y se programan ahora.  Las tareas programadas son tareas que se han iniciado en código pero no se han ejecutado todavía.  Por consiguiente, las columnas **Asignación de subproceso** y **Ubicación** están vacías.  
  
     Observe la ventana **Pilas paralelas** de nuevo.  El encabezado de cada cuadro tiene una información sobre herramientas que muestra los identificadores y los nombres de los subprocesos.  Cambie a la vista de tareas en la ventana **Pilas paralelas**.  Desplace el puntero del mouse sobre un encabezado para ver el identificador, el nombre y el estado de la tarea, como se muestra en la siguiente ilustración.  
  
     ![Información sobre herramientas de encabezado en la ventana Pilas paralelas](../debugger/media/pdb_walkthrough_11.png "PDB\_Walkthrough\_11")  
  
     Puede agrupar las tareas por columna.  En la ventana **Tareas paralelas**, haga clic con el botón secundario en el encabezado de columna **Estado** y, a continuación, haga clic en **Agrupar por estado**.  La siguiente ilustración muestra la ventana **Tareas paralelas** agrupadas por estado.  
  
     ![Tareas agrupadas en la ventana Tareas paralelas](../debugger/media/pdb_walkthrough_12.png "PDB\_Walkthrough\_12")  
  
     También puede agrupar por cualquier otra columna.  Agrupando las tareas, se puede concentrar en un subconjunto de tareas.  Cada grupo contraíble tiene un recuento de los elementos que están agrupados.  También puede marcar rápidamente todos los elementos del grupo haciendo clic en el botón **Marcar** a la derecho del botón **Contraer**.  
  
     ![Pilas agrupadas en la ventana Pilas paralelas](../debugger/media/pdb_walkthrough_12a.png "PDB\_Walkthrough\_12A")  
  
     La última característica para examinar de la ventana **Tareas paralelas** es el menú contextual que se muestra al hacer clic con el botón secundario en una tarea.  
  
     ![Menú contextual en la ventana Tareas paralelas](../debugger/media/pdb_walkthrough_12b.png "PDB\_Walkthrough\_12B")  
  
     El menú contextual muestra comandos diferentes, dependiendo del estado de la tarea.  Los comandos pueden incluir **Copiar**, **Seleccionar todo**, **Presentación hexadecimal**, **Cambiar a tarea**, **Inmovilizar subproceso asignado**, **Inmovilizar todos los subprocesos excepto este**, **Reanudar subproceso asignado** y **Marcar**.  
  
     Puede inmovilizar el subproceso subyacente de una o varias tareas, y puede inmovilizar todos los subprocesos exceptuando el asignado.  Un subproceso inmovilizado se representa en la ventana **Tareas paralelas** como en la ventana **Subprocesos**, por un icono de *pausa* azul.  
  
## Resumen  
 En este tutorial se han mostrado las ventanas del depurador **Tareas paralelas** y **Pilas paralelas**.  Utilice estas ventanas en los proyectos reales que utilizan código multithreading.  Puede examinar código paralelo escrito en C\+\+, C\# o Visual Basic.  
  
## Vea también  
 [Debugging Multithreaded Applications](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Conceptos básicos del depurador](../debugger/debugger-basics.md)   
 [Depurar código administrado](../debugger/debugging-managed-code.md)   
 [Parallel Programming](../Topic/Parallel%20Programming%20in%20the%20.NET%20Framework.md)   
 [Runtime de simultaneidad](/visual-cpp/parallel/concrt/concurrency-runtime)   
 [Uso de la ventana Tareas paralelas](../debugger/using-the-parallel-stacks-window.md)   
 [Usar la ventana Tareas](../debugger/using-the-tasks-window.md)