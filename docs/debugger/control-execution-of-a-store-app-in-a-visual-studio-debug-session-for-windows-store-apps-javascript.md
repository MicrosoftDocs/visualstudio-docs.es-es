---
title: "Controlar la ejecuci&#243;n de una aplicaci&#243;n de la Tienda en una sesi&#243;n de depuraci&#243;n de Visual Studio para aplicaciones de la Tienda Windows (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
ms.assetid: 60159535-61ec-466a-a4a6-115ec72a8af5
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Controlar la ejecuci&#243;n de una aplicaci&#243;n de la Tienda en una sesi&#243;n de depuraci&#243;n de Visual Studio para aplicaciones de la Tienda Windows (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este inicio rápido se muestra cómo navegar en el depurador de Visual Studio y cómo ver el estado del programa en una sesión.  
  
 Está dirigido a los desarrolladores que son nuevos en la depuración con Visual Studio, así como a los desarrolladores que quieran obtener más información sobre la navegación en una sesión de depuración de Visual Studio. No enseña el arte de la depuración. Las funciones del código de ejemplo están diseñadas únicamente para demostrar los procedimientos de depuración descritos en este tema. Las funciones no usan los procedimientos recomendados para el diseño de aplicaciones o funciones. De hecho, descubrirá rápidamente que las funciones y la propia aplicación no hacen mucho.  
  
 Las secciones de este inicio rápido se han diseñado para ser lo más independiente posible, por lo que puede omitir cualquier sección que incluya información que ya conoce. Tampoco es necesario que cree una aplicación de ejemplo. Sin embargo, lo recomendamos y hemos hecho que el proceso sea lo más sencillo posible.  
  
 **Métodos abreviados de teclado del depurador.** La navegación en el depurador de Visual Studio está optimizada para el mouse y el teclado. Muchos de los pasos de este tema incluyen la tecla de aceleración o la tecla de método abreviado del teclado en un comentario entre paréntesis. Por ejemplo, \(teclado: F5\) indica que la tecla F5 inicia o continúa la ejecución del depurador.  
  
> [!NOTE]
>  **Patrón de módulo**  
>   
>  A menudo, las aplicaciones de la Tienda Windows usan el *patrón de módulo* de JavaScript para encapsular datos y funciones en una página. El patrón de módulo usa una única clausura, anónima y autoejecutable, para separar la funcionalidad de la página del espacio de nombres global. En este tema, llamamos a esa función el *módulo*.  
  
## En este tema  
 Aprenderá a realizar lo siguiente:  
  
 [Crear la aplicación de ejemplo](#BKMK_Create_the_sample_app)  
  
 [Configurar y ejecutar hasta un punto de interrupción, depurar paso a paso una función y examinar los datos del programa](#BKMK_Set_and_run_to_a_breakpoint__step_into_a_function__and_examine_program_data)  
  
 [Depurar paso a paso por, en y fuera de las funciones](#BKMK_Step_into__over__and_out_of_functions)  
  
 [Establecer un punto de interrupción condicional, ejecutar hasta el cursor y ver una variable](#BKMK_Set_a_conditional_breakpoint__run_to_the_cursor__and_visualize_a_variable)  
  
 [Ver los datos de la variable en la ventana Variables locales](#BKMK_View_variable_data_in_the_Locals_window)  
  
-   [Ver datos de la variable y la cadena de prototipo de un objeto](#BKMK_View_variable_data_and_the_prototype_chain_of_an_object)  
  
-   [Examinar los datos de la cadena de ámbito](#BKMK_Examine_scope_chain_data)  
  
 [Navegar hasta el código con la ventana Pila de llamadas](#BKMK_Navigate_to_code_by_using_the_Call_Stack_window)  
  
##  <a name="BKMK_Create_the_sample_app"></a> Crear la aplicación de ejemplo  
 La depuración trata del código, por lo que la aplicación de ejemplo solo usa el marco de la aplicación de la Tienda Windows para crear un archivo de origen en el que puede ver cómo funciona la navegación de una sesión de depuración y cómo examinar el estado del programa. Todo el código que invoca se llama desde la función `module` del archivo default.js. No se agregan controles ni se administra ningún evento.  
  
1.  **Cree una aplicación de la Tienda Windows de JavaScript en blanco.** Abra Visual Studio. En la página principal, seleccione el vínculo de **Nuevo proyecto**. En el cuadro de diálogo **Nuevo proyecto**, seleccione **JavaScript** en la lista **Instalado** y luego elija **Tienda Windows**. En la lista de plantillas de proyecto, seleccione **Aplicación vacía**. Visual Studio crea una nueva solución y un proyecto, y muestra el archivo default.htm en el editor de código.  
  
     Observe los archivos de script que se cargan en la página.  
  
    -   Los archivos `base.js` y `ui.js` crean la **Biblioteca de Windows para JavaScript**. La Biblioteca de Windows para JavaScript es un conjunto de archivos JavaScript y CSS que facilitan la creación de aplicaciones de la Tienda Windows con JavaScript. Se usa junto con HTML, CSS y Windows Runtime para crear la aplicación.  
  
    -   El código se inicia en el archivo `default.js` .  
  
2.  **Abra el archivo de origen default.js.** En el Explorador de soluciones, abra el nodo **js** y seleccione `default.js`.  
  
3.  **Reemplace el contenido de la página por el código de ejemplo.** Elimine todo el contenido del archivo `default.js`. Siga este vínculo: [Código de ejemplo de navegación del depurador \(JavaScript\)](../debugger/debugger-navigation-sample-code-javascript.md) y, después, copie el código que aparece en la sección de JavaScript en el portapapeles. \(Seleccione **Atrás** en el explorador o el visor de ayuda para volver a esta página de inicio rápido\). En el editor de Visual Studio, pegue el código en el `default.js` vacío. Presione **CTRL\+ S** para guardar el archivo.  
  
 Ahora, puede seguir los ejemplos de este tema.  
  
##  <a name="BKMK_Set_and_run_to_a_breakpoint__step_into_a_function__and_examine_program_data"></a> Configurar y ejecutar hasta un punto de interrupción, depurar paso a paso una función y examinar los datos del programa  
 La manera más común de iniciar una sesión de depuración es seleccionar **Iniciar depuración** desde el menú **Depurar** \(teclado: F5\). Se inicia la aplicación y sigue ejecutándose hasta que se alcanza un punto de interrupción, se suspende manualmente la ejecución, se produce una excepción o la aplicación finaliza.  
  
 Cuando se suspende la ejecución en el depurador, se puede ver el valor de una variable activa en la información sobre datos que aparece si se mantiene el cursor sobre la variable.  
  
 Después de suspender la ejecución de la aplicación \(lo que también se conoce como interrupción en el depurador\), puede controlar la manera en que se ejecuta el resto del código de programa. Puede continuar línea por línea, pasando de una llamada de función a la propia función, o puede ejecutar una función a la que se ha llamado en un solo paso. Se llama a estos procedimientos al recorrer paso a paso la aplicación. También puede reanudar la ejecución estándar de la aplicación, ejecutando hasta el siguiente punto de interrupción configurado o hasta la línea en la que se ha colocado el cursor. Puede detener la sesión de depuración en cualquier momento. El depurador se ha diseñado para realizar las operaciones de limpieza necesarias y salir de la ejecución.  
  
###  <a name="BKMK_Example_1"></a> Ejemplo 1  
 En este ejemplo, se configura un punto de interrupción en el cuerpo de la función `module` de `default.js` cuando se llama a la primera de nuestras instrucciones de usuario. A continuación, puede depurar paso a paso por instrucciones la función, ver los valores de las variables en la información sobre datos del depurador y detener la depuración.  
  
1.  **Establezca un punto de interrupción.** Configure un punto de interrupción en la instrucción `callTrack = "module function";` que se produce justo después de la llamada a `app.start()`. Seleccione la línea en el medianil sombreado del editor de código fuente \(teclado: sitúe el cursor en la línea y presione la tecla **F9**\).  
  
     ![Establecer un punto de interrupción en example1](~/docs/debugger/media/dbg_jsnav_example1_breakpoint.png "DBG\_JSNAV\_example1\_breakpoint")  
  
     El icono de punto de interrupción aparece en el medianil.  
  
2.  **Ejecute hasta el punto de interrupción.** Inicie la sesión de depuración. Para ello, elija **Iniciar depuración** en el menú **Depurar** \(teclado: F5\).  
  
     La aplicación comienza a ejecutarse y suspende la ejecución inmediatamente antes de la instrucción donde configuró el punto de interrupción. El icono de la línea actual que aparece en el margen identifica su ubicación. La instrucción actual se resalta.  
  
     ![Ejecutar hasta el punto de interrupción](~/docs/debugger/media/dbg_jsnav_example1_run_to_breakpoint.png "DBG\_JSNAV\_example1\_run\_to\_breakpoint")  
  
     Ahora controla la ejecución de la aplicación y puede examinar el estado del programa a medida que recorre paso a paso sus instrucciones.  
  
3.  **Depure paso a paso por instrucciones la función.** En el menú **Depurar**, seleccione **Paso a paso por instrucciones** \(teclado: **F11**\).  
  
     ![Ir a una línea de código](~/docs/debugger/media/dbg_jsnav_example1_step_into.png "DBG\_JSNAV\_example1\_step\_into")  
  
     Observe que el depurador se mueve a la siguiente línea, que es una llamada a la función `example1`. Seleccione **Depurar paso a paso** de nuevo. El depurador se mueve a la primera línea de código de la función `example1`. La línea resaltada no se ha ejecutado, pero la función se ha cargado en la pila de llamadas y se ha asignado la memoria para las variables locales.  
  
4.  Al depurar paso a paso por instrucciones una línea de código, el depurador realiza una de las siguientes acciones:  
  
    -   Si la instrucción siguiente no es una llamada a una función de la solución, el depurador ejecuta la instrucción, pasa a la siguiente instrucción y, después, suspende la ejecución.  
  
    -   Si la instrucción es una llamada a una función de la solución, el depurador se mueve a la primera línea de la función a la que se llama y suspende la ejecución.  
  
     Siga con la depuración paso a paso por las instrucciones de `example1` hasta que haya alcanzado el punto de salida. El depurador resalta la llave de cierre de la función.  
  
5.  **Vea los valores de la variable en la información sobre datos.** Siga con la depuración paso a paso por las instrucciones de `example1` hasta que haya alcanzado el punto de salida. El depurador resalta la llave de cierre de la función. Al pausar el mouse en un nombre de variable, el nombre y el valor de la variable se muestran en la información sobre datos.  
  
     ![Ver valores variables en la información sobre datos](~/docs/debugger/media/dbg_jsnav_data_tip.png "DBG\_JSNAV\_data\_tip")  
  
6.  **Agregue una inspección para la variable callTrack.** La variable `callTrack` se usa en esta guía de inicio rápido para mostrar las funciones a las que se llama en los ejemplos. Para facilitar la visualización del valor de la variable, es necesario que se agregue a una ventana Inspección. Seleccione el nombre de la variable en el editor y luego elija **Agregar inspección** en el menú contextual.  
  
     ![Examinar una variable](../debugger/media/dbg_jsnav_watch_window.png "DBG\_JSNAV\_watch\_window")  
  
     Puede inspeccionar múltiples variables en una ventana Inspección. Los valores de las variables inspeccionadas, al igual que los valores de las ventanas de información sobre datos, se actualizan cada vez que se suspende la ejecución. Las variables inspeccionadas se guardan en las sesiones de depuración.  
  
7.  **Detenga la depuración.** En el menú **Depurar**, seleccione **Detener depuración** \(teclado: **Mayús\+F5**\). Esto finaliza la sesión de depuración.  
  
##  <a name="BKMK_Step_into__over__and_out_of_functions"></a> Depurar paso a paso por, en y fuera de las funciones  
 A diferencia de la depuración paso a paso por instrucciones de una función a la que llama una función principal, la depuración paso a paso por procedimientos de una función ejecuta la función secundaria y suspende la ejecución de la función de llamada mientras se reanuda la primaria. Puede depurar paso a paso en una función cuando conozca el modo en que funciona la función y esté seguro de que su ejecución no afectará al problema que está investigando.  
  
 La depuración paso a paso por procedimientos de una línea de código que no contiene una llamada de función ejecuta la línea de igual manera que con la depuración paso a paso por instrucciones.  
  
 La depuración paso a paso para salir de una función secundaria sigue con la ejecución de la función y la suspende cuando la función vuelve a su función de llamada. Puede ser conveniente depurar una función larga paso a paso hasta salir si ha determinado que el resto de la función no es significativo.  
  
 La función se ejecuta cuando se depura paso a paso tanto por procedimientos como hasta salir.  
  
 ![Ir a un método, saltarlo o salir de este](../debugger/media/dbg_basics_stepintooverout.png "DBG\_Basics\_StepIntoOverOut")  
  
###  <a name="BKMK_Example_2"></a> Ejemplo 2  
 En este ejemplo, se depura paso a paso por, en y fuera de funciones.  
  
1.  **Llame a la función example2 de la función de módulo.** Edite la función `module` y reemplace la línea siguiente a `var callTrack = "module function"` por `example2();`.  
  
     ![Llamar a la función example2](~/docs/debugger/media/dbg_jsnav_example2.png "DBG\_JSNAV\_example2")  
  
2.  **Ejecute hasta el punto de interrupción.** Inicie la sesión de depuración. Para ello, elija **Iniciar depuración** en el menú **Depurar** \(teclado: F5\). El depurador suspende la ejecución en el punto de interrupción.  
  
3.  **Depure la línea de código paso a paso por procedimientos.** En el menú **Depurar**, seleccione **Paso a paso por procedimientos** \(teclado: F10\). El depurador ejecuta la instrucción `var callTrack = "module function"` de la misma manera que si se depurase paso a paso por instrucciones.  
  
4.  **Depure paso a paso por instrucciones example2 y example2\_a.** Seleccione la tecla **F11** para depurar paso a paso por la función `example2`. Siga con la depuración paso a paso por las instrucciones `example2` hasta llegar a la línea `var x = example2_a();`. De nuevo, depure paso a paso por esta línea para desplazarse al punto de entrada de `example2_a`. Continúe con la depuración paso a paso por instrucciones de cada instrucción de `example2_a` hasta volver a `example2`.  
  
     ![Saltar una función](~/docs/debugger/media/dbg_jsnav_example2_a.png "DBG\_JSNAV\_example2\_a")  
  
5.  **epure una función paso a paso por procedimientos.** Tenga en cuenta que la siguiente línea de `example2`, `var y = example2_a();` es básicamente la misma que la línea anterior. Puede depurarla paso a paso por procedimientos sin ningún problema. Seleccione la tecla **F10** para pasar de la reanudación de `example2` a esta segunda llamada a `example2_a`. Tenga en cuenta que la cadena `callTrack` indica que la función `example2_a` se ejecutó dos veces.  
  
6.  **Depure una función paso a paso hasta salir.** Seleccione la tecla **F11** para depurar paso a paso por la función `example2_b`. Tenga en cuenta que `example2_b` no es muy diferente de `example2_a`. Para depurar paso a paso fuera de la función, seleccione **Depurar paso a paso fuera de** en el menú **Depurar** \(teclado: **Mayús\+F11**\). Tenga en cuenta que la variable `callTrack` indica que se ha ejecutado `example2_b` y que el depurador ha vuelto al punto en el que `example2` se reanuda.  
  
7.  **Detenga la depuración.** En el menú **Depurar**, seleccione **Detener depuración** \(teclado: **Mayús\+F5**\). Esto finaliza la sesión de depuración.  
  
##  <a name="BKMK_Set_a_conditional_breakpoint__run_to_the_cursor__and_visualize_a_variable"></a> Establecer un punto de interrupción condicional, ejecutar hasta el cursor y ver una variable  
 Un punto de interrupción condicional especifica una condición que hace que el depurador suspenda la ejecución. La condición se especifica mediante cualquier expresión de código que se pueda evaluar como verdadera o falsa. Por ejemplo, en una función a la que se llama a menudo, podría usar un punto de interrupción condicional para examinar el estado del programa solamente cuando una variable alcance un valor determinado.  
  
 Ejecutar hasta el cursor es igual que establecer un punto de interrupción único. Cuando se suspende la ejecución, puede seleccionar una línea de código fuente y reanudar la ejecución hasta la línea seleccionada. Por ejemplo, se puede recorrer un bucle en una función y determinar que el código del bucle se está ejecutando correctamente. En lugar de recorrer todas las iteraciones del bucle, puede ejecutar hasta el cursor colocado que está después de la ejecución del bucle.  
  
 A veces, es difícil ver el valor de una variable en la fila de la información sobre datos u otra ventana de datos. El depurador puede mostrar cadenas, HTML y XML en un visualizador de texto que presenta una vista con formato del valor en una ventana desplazable.  
  
###  <a name="BKMK_Example_3"></a> Ejemplo 3  
 En este ejemplo, se establece un punto de interrupción condicional para interrumpir la ejecución en una iteración concreta de un bucle y, después, se ejecuta hasta el cursor situado después del bucle. También se ve el valor de una variable en un visualizador de texto.  
  
1.  **Llame a la función example3 de la función de módulo.** Edite la función `module` y reemplace la línea siguiente a `var callTrack = "module function";` por la línea `example3();`.  
  
     ![Llamada de example3](~/docs/debugger/media/dbg_jsnav_example3.png "DBG\_JSNAV\_example3")  
  
2.  **Ejecute hasta el punto de interrupción.** Inicie la sesión de depuración seleccionando **Iniciar depuración** en el menú **Depurar** \(teclado: **F5**\). El depurador suspende la ejecución en el punto de interrupción de la función `module`.  
  
3.  **Depure paso a paso por instrucciones la función example3.** Seleccione **Depurar paso a paso por** en el menú **Depurar** \(teclado: **F11**\) para desplazarse al punto de entrada de la función `example3`. Continúe con la depuración paso a paso por la función hasta que se hayan iterado uno o dos bucles del bloque `for`. Tenga en cuenta que se tardaría demasiado tiempo en recorrer paso a paso las 1000 iteraciones.  
  
4.  **Establezca un punto de interrupción condicional.** En el medianil izquierdo de la ventana de código, haga clic con el botón derecho en la línea `s += i.toString() + "\n";` y seleccione **Condición** en el menú contextual.  
  
     Seleccione la casilla **Condición** y escriba `i == 500;` en el cuadro de texto. Seleccione la opción **Es true** y seleccione **Aceptar**. El punto de interrupción permite comprobar el valor en la iteración número 500 del bucle `for`. El aspa blanca le permite distinguir el icono de un punto de interrupción condicional.  
  
     ![Icono de punto de interrupción condicional](~/docs/debugger/media/dbg_jsnav_breakpoint_condition_icon.png "DBG\_JSNAV\_Breakpoint\_Condition\_icon")  
  
5.  **Ejecute hasta el punto de interrupción.** En el menú **Depurar**, seleccione **Continuar** \(teclado: **F5**\). Pause en `i` para confirmar que el valor actual de `i` es 500. Tenga en cuenta también que la variable `s` se representa como una línea única y que es mucho más larga que la ventana de información sobre datos.  
  
6.  **Visualice una variable de cadena.** Haga clic en el icono de lupa en la información sobre datos de `s`.  
  
     Aparece la ventana del visualizador de texto. El valor de la cadena se muestra como una cadena de varias líneas.  
  
     ![Depurar visualizador de texto](../debugger/media/dbg_jsnav_text_visualizer.png "DBG\_JSNAV\_Text\_Visualizer")  
  
7.  **Ejecute hasta el cursor.** Seleccione la línea `callTrack += "->example3";` y seleccione **Ejecutar hasta el cursor** en el menú contextual \(teclado: **Ctrl\+F10**\). El depurador completa las iteraciones del bucle y, después, suspende la ejecución en la línea.  
  
8.  **Detenga la depuración.** En el menú **Depurar**, seleccione **Detener depuración** \(teclado: **Mayús\+F5**\). Esto finaliza la sesión de depuración.  
  
###  <a name="BKMK_Use_Run_to_Cursor_to_return_to_your_code_and_delete_a_breakpoint"></a> Usar Ejecutar hasta el cursor para volver al código y eliminar un punto de interrupción  
 Ejecutar hasta el cursor puede ser muy útil tras la depuración paso a paso por instrucciones del código de biblioteca de Microsoft o de un tercero. Aunque recorrer el código de biblioteca puede proporcionar información útil, suele tardar mucho tiempo. Por lo general, le interesa mucho más su propio código. En este ejercicio muestra cómo hacerlo.  
  
1.  **Establezca un punto de interrupción en la llamada app.start.** En la función `module`, establezca un punto de interrupción en la línea `app.start()`  
  
2.  **Ejecute hasta el punto de interrupción y depure paso a paso por instrucciones la función de biblioteca.**  
  
     Al depurar paso a paso por `app.start()`, el editor muestra el código en `base.js`. Depure paso a paso por instrucciones unas cuantas líneas más.  
  
3.  **Depure paso a paso por procedimientos y para salir de las funciones.** A medida que realiza la depuración paso a paso por procedimientos \(**F10**\) y paso a paso para salir \(**MAYÚS\+F11**\) del código de `base.js`, puede llegar a la conclusión de que examinar la complejidad y la longitud de la función de inicio no es lo que quiere hacer.  
  
4.  **Configure el cursor en el código y ejecute hasta él.** Vuelva al archivo `default.js` del editor de código. Seleccione la primera línea de código después de `app.start()` \(no puede ejecutar hasta un comentario o una línea en blanco\). Seleccione **Ejecutar hasta el cursor** en el menú contextual. El depurador continúa la ejecución de la función app.start y suspende la ejecución en el punto de interrupción.  
  
##  <a name="BKMK_View_variable_data_in_the_Locals_window"></a> Ver los datos de la variable en la ventana Variables locales  
 Las ventanas Variables locales son una vista de árbol de los parámetros y las variables de la cadena de ámbito de la función que se ejecuta actualmente.  
  
###  <a name="BKMK_View_variable_data_and_the_prototype_chain_of_an_object"></a> Ver datos de la variable y la cadena de prototipo de un objeto  
  
1.  **Agregue un objeto de matriz a la función de módulo.** Edite la función `module` y reemplace la línea siguiente a `var callTrack = "module function"` por `var myArray = new Array(1, 2, 3);`  
  
     ![Definición de myArray](~/docs/debugger/media/dbg_jsnav_myarray.png "DBG\_JSNAV\_myArray")  
  
2.  **Ejecute hasta el punto de interrupción.** Inicie la sesión de depuración seleccionando **Iniciar depuración** en el menú **Depurar** \(teclado: **F5**\). El depurador suspende la ejecución en el punto de interrupción. Depure paso a paso por instrucciones hasta la línea.  
  
3.  **Abra la ventana Variables locales.** En el menú **Depurar**, diríjase a **Ventanas** y seleccione **Variables locales**. \(Teclado: Alt\+4\).  
  
4.  **Examine las variables locales de la función de módulo**. Las ventanas Variables locales muestran las variables de la función que se ejecuta actualmente \(`module`\) como nodos de nivel superior del árbol. Al introducir una función, JavaScript crea todas las variables y les da un valor de `undefined`. Las funciones que se definen en la función tienen el texto como un valor.  
  
     ![Ventana Locales](../debugger/media/dbg_jsnav_locals_window.png "DBG\_JSNAV\_Locals\_window")  
  
5.  **Recorra paso a paso las definiciones de callTrack y myArray.** Las variables callTrack y myArray se encuentran en la ventana Variables locales. Depure paso a paso en \(**F10**\) las dos definiciones y observe que los campos **Valor** y **Tipo** han cambiado. La ventana Variables locales resalta los valores de las variables que han cambiado desde la última interrupción.  
  
6.  **Examine el objeto myArray**. Expanda la variable `myArray`. Cada elemento de la matriz se muestra en el nodo **\[prototipo\]** que contiene la jerarquía de herencia del objeto `Array`. Expanda este nodo.  
  
     ![Cadena de prototipo en la ventana Locales](../debugger/media/dbg_jsnav_locals_proto_chain.png "DBG\_JSNAV\_Locals\_proto\_chain")  
  
    -   El nodo **Métodos** muestra todos los métodos del objeto `Array`.  
  
    -   El nodo **\[prototipo\]** contiene el prototipo del objeto `Object` del que se deriva `Array`. Los nodos **\[prototipo\]** pueden ser recursivos. Cada objeto primario de una jerarquía de objetos se describe en el nodo **\[prototipo\]** de su secundario.  
  
7.  **Detenga la depuración.** En el menú **Depurar**, seleccione **Detener depuración** \(teclado: Mayús\+F5\). Esto finaliza la sesión de depuración.  
  
##  <a name="BKMK_Examine_scope_chain_data"></a> Examinar los datos de la cadena de ámbito  
 La *cadena de ámbito* de una función incluye todas las variables activas y accesibles para la función. Las variables globales son parte de la cadena de ámbito, como los objetos \(incluidas las funciones\) que se definen en la función que define la función que se ejecuta actualmente. Por ejemplo, la variable `callTrack` que se define en la función `module` de `default.js` es accesible para cualquier función definida en la función `module`. Cada ámbito se muestra por separado en la ventana Variables locales.  
  
-   Las variables de la función que se ejecuta actualmente se muestran en la parte superior de la ventana.  
  
-   Las variables de cada ámbito de función de la cadena de ámbito se muestran en el nodo **\[Ámbito\]** de la función. Las funciones de ámbito se muestran por su orden en la cadena, desde la función que define la función actual hasta la más externa de la cadena.  
  
-   El nodo **\[Globales\]** muestra los objetos globales que se definen fuera de una función.  
  
 Las cadenas de ámbito pueden ser confusas y se ilustran mejor con un ejemplo. En el ejemplo siguiente, puede ver cómo la función `module` crea su propio ámbito y cómo puede crear otro nivel de ámbito mediante la creación de una clausura.  
  
###  <a name="BKMK_Example_4"></a> Ejemplo 4  
  
1.  **Llame a la función example4 desde la función de módulo.** Edite la función `module` y reemplace la línea siguiente a `var callTrack = "module function"` por `example4()`:  
  
     ![Llamada de example4](~/docs/debugger/media/dbg_jsnav_example4.png "DBG\_JSNAV\_example4")  
  
2.  **Ejecute hasta el punto de interrupción.** Inicie la sesión de depuración seleccionando **Iniciar depuración** en el menú **Depurar** \(teclado: **F5**\). El depurador suspende la ejecución en el punto de interrupción.  
  
3.  **Abra la ventana Variables locales.** Si es necesario, en el menú **Depurar**, apunte a **Ventanas** y seleccione **Variables locales**. \(Teclado: **Alt\+4**\). Observe que la ventana muestra todas las variables y las funciones de la función `module`, así como que contiene un nodo **\[Globales\]**.  
  
4.  **Examine las variables globales.** Expanda el nodo **\[Globales\]**. Biblioteca de Windows para JavaScript configuró los objetos y las variables de Globales. Puede agregar sus propias variables al ámbito global.  
  
5.  **Depure paso a paso por instrucciones example4 y examine sus variables locales y de ámbito**. Depure paso a paso por instrucciones\(teclado: **F11**\) la función `example4`. Dado que `example4` se define en la función `module`, la función `module` se convierte en el ámbito primario.`example4` puede llamar a cualquiera de las funciones de la función `module` y acceder a sus variables. Expanda el nodo **\[Ámbito\]** de la ventana Variables locales y observe que contiene las mismas variables que la función `module`.  
  
     ![Ámbitos del método example4](../debugger/media/dbg_jsnav_locals_example4_scope.png "DBG\_JSNAV\_Locals\_example4\_scope")  
  
6.  **Depure paso a paso por instrucciones example4\_a y examine sus variables locales y de ámbito**. Continúe con la depuración paso a paso por instrucciones de `example4` y la llamada a `example4_a`. Tenga en cuenta que las variables locales son ahora de `example4_a` y que el nodo **\[Ámbito\]** sigue conservando las variables de la función `module`. Aunque las variables de `example4` estén activas, `example4_a` no puede acceder a ellas y ya no forman parte de la cadena de ámbito.  
  
7.  **Depure paso a paso por instrucciones multipyByA y examine sus variables locales y de ámbito**. Recorra paso a paso el resto de `example4_a` y depure paso a paso por instrucciones la línea `var x = multilpyByA(b);`.  
  
     La variable de la función `multipyByA` se ha establecido en la función `multiplyClosure` que es una *clausura*.`multipyClosure` define y devuelve una función interna, `mulitplyXby`, y captura \(cierra\) el parámetro y la variable. En una clausura, la función interna devuelta tiene acceso a los datos de la función externa y crea su propio nivel de ámbito.  
  
     Al depurar paso a paso por instrucciones `var x = multilpyByA(b);`, se mueve a la línea `return a * b;` de la función interna `mulitplyXby`.  
  
8.  En la ventana Variables locales, solo el parámetro `b` se muestra como una variable local en `multiplyXby`, pero se agrega un nuevo nivel **\[Ámbito\]**. Al expandir este nodo, verá que contiene los parámetros, las funciones y las variables de `multiplyClosure`, incluida la variable `a` a la que se llama en la primera línea de `multiplyXby`. Una comprobación rápida del segundo nodo **\[Ámbito\]** revela las variables de función de módulo, a las que `multiplyXby` accede en la línea siguiente.  
  
     ![Ámbitos de un cierre en la ventana Locales](../debugger/media/dbg_jsnav_scope_mulitplyxby.png "DBG\_JSNAV\_scope\_mulitplyXby")  
  
9. **Detenga la depuración.** En el menú **Depurar**, seleccione **Detener depuración** \(teclado: **Mayús\+F5**\). Esto finaliza la sesión de depuración.  
  
##  <a name="BKMK_Navigate_to_code_by_using_the_Call_Stack_window"></a> Navegar hasta el código con la ventana Pila de llamadas  
 La pila de llamadas es una estructura de datos que contiene información sobre las funciones que se ejecutan en el subproceso actual de la aplicación. Cuando se alcanza un punto de interrupción, la ventana Pila de llamadas muestra una lista de todas las funciones que están activas en la pila. La función que se ejecuta actualmente se encuentra en la parte superior de la lista de la ventana Pila de llamadas. La función que inicia el subproceso se encuentra en la parte inferior de la lista. Las funciones que se encuentran entre estas muestran la ruta de acceso de la llamada desde la función de inicio hasta la función actual.  
  
 Además de mostrar la ruta de acceso de la llamada hasta la función que se ejecuta actualmente, la ventana Pila de llamadas se puede usar para navegar hasta el código del editor de código. Esta funcionalidad puede ser valiosa cuando trabaja con varios archivos y quiere desplazarse rápidamente a una función determinada.  
  
###  <a name="BKMK_Example_5"></a> Ejemplo 5  
 En este ejemplo, se depura paso a paso por una ruta de acceso de llamada que contiene cinco funciones definidas por el usuario.  
  
1.  **Llame a la función example5 de la función de módulo.** Edite la función `module` y reemplace la línea siguiente a `var callTrack = "module function";` por la línea `example5();`.  
  
     ![Llamada de example5](~/docs/debugger/media/dbg_jsnav_example5.png "DBG\_JSNAV\_example5")  
  
2.  **Ejecute hasta el punto de interrupción.** Inicie la sesión de depuración seleccionando **Iniciar depuración** en el menú **Depurar** \(teclado: **F5**\). El depurador suspende la ejecución en el punto de interrupción de la función de módulo.  
  
3.  **Abra la ventana Pila de llamadas.** En el menú **Depurar**, seleccione **Ventanas** y seleccione **Pila de llamadas** \(teclado: Alt\+7\). Tenga en cuenta que la ventana Pila de llamadas muestra dos funciones:  
  
    -   **Código global** es el punto de entrada de la función `module` en la parte inferior de la pila de llamadas.  
  
    -   **Función anónima** muestra la línea de la función `module` donde se suspende la ejecución. Se trata de la parte superior de la pila de llamadas.  
  
4.  **Depure paso a paso por instrucciones las funciones para alcanzar la función example5\_d.** Seleccione **Depurar paso a paso** del menú **Depurar** \(teclado: **F11**\) para ejecutar las llamadas en la ruta de acceso de la llamada hasta alcanzar el punto de entrada de la función example5\_d. Tenga en cuenta que cada vez que una función llama a una función, se guarda el número de línea de la función de llamada y la función a la que se llama se coloca en la parte superior de la pila. El número de línea de la función de llamada es el punto en el que la función de llamada suspende la ejecución. Una flecha amarilla apunta a la función que se ejecuta actualmente.  
  
     ![Ventana Pila de llamadas](../debugger/media/dbg_jsnav_callstack_windows.png "DBG\_JSNAV\_CallStack\_windows")  
  
5.  **Use la ventana Pila de llamadas para navegar hasta el código example5\_a y establecer un punto de interrupción.** En la ventana Pila de llamadas, seleccione el elemento de lista `example5_a` y seleccione **Ir a origen** en el menú contextual. El editor de código configura el cursor en la línea de retorno de la función. Configure un punto de interrupción en esta línea. Tenga en cuenta que no se cambia la línea de ejecución actual. Solo se mueve el cursor del editor.  
  
6.  **Depure paso a paso por instrucciones las funciones y ejecute hasta el punto de interrupción.** Continúe con la depuración paso a paso por `example5_d`. Tenga en cuenta que, al volver de la función, se desconecta la pila de llamadas. Presione **F5** para continuar con la ejecución del programa. Se detendrá en el punto de interrupción creado en el paso anterior.  
  
7.  **Detenga la depuración.** En el menú **Depurar**, seleccione **Detener depuración** \(teclado: **Mayús\+F5**\). Esto finaliza la sesión de depuración.  
  
## Vea también  
 [Iniciar una sesión de depuración \(JavaScript\)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md)   
 [Quickstart: Debugger navigation \(JavaScript\)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md)   
 [Inicio rápido: Depurar HTML y CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Desencadenar eventos de suspensión, reanudación y en segundo plano para aplicaciones de la Tienda Windows](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)   
 [Depurar aplicaciones en Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)