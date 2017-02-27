---
title: "Editar pruebas de IU codificadas mediante el editor de pruebas de IU codificadas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codedUItest.testeditor"
helpviewer_keywords: 
  - "prueba de IU codificada, Editor de pruebas de IU codificadas"
ms.assetid: 76435c4b-593e-43a3-a9fe-709a7f9f5e0f
caps.latest.revision: 40
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 40
---
# Editar pruebas de IU codificadas mediante el editor de pruebas de IU codificadas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

el Editor de pruebas de IU codificadas permite modificar fácilmente este tipo de pruebas. Con el editor de pruebas de IU codificadas puede localizar, ver y editar las propiedades de los métodos de prueba y acciones de IU. Además, puede usar la asignación de controles de IU para ver y editar sus controles correspondientes.  
  
 **Requisitos**  
  
-   Visual Studio Enterprise  
  
## ¿Por qué debo hacerlo?  
 El uso del editor de pruebas de IU codificadas es más rápido y eficaz que editar el código en los métodos de pruebas de IU codificadas con el editor de código. Con el editor de pruebas de IU codificadas puede usar la barra de herramientas y los menús contextuales para ubicar y modificar rápidamente los valores de propiedad asociados a acciones y controles de la interfaz de usuario. Por ejemplo, puede usar la barra de herramientas del editor de pruebas de IU codificadas para llevar a cabo los siguientes comandos:  
  
 ![Editor de pruebas de IU](../test/media/uitesteditor.png "UITestEditor")  
  
1.  [Buscar](../ide/finding-and-replacing-text.md) le ayuda a localizar las acciones y controles de la interfaz de usuario.  
  
2.  [Eliminar](#CodedUITestEditor_DeleteUIActions) quita las acciones no deseadas de la interfaz de usuario.  
  
3.  **Cambiar nombre** cambia los nombres de los controles y los métodos de prueba.  
  
4.  **Propiedades** abre la ventana Propiedades del elemento seleccionado.  
  
5.  [Dividir en un método nuevo](#CodedUITestEditor_SplitMethods) permite modularizar las acciones de la interfaz de usuario.  
  
6.  [Mover código](#CodedUITestEditor_MoveMethods) agrega código personalizado a los métodos de prueba.  
  
7.  [Insertar retraso antes](#CodedUITestEditor_InsertDelay) agrega una pausa en milisegundos antes de una acción de interfaz de usuario.  
  
8.  [Buscar control de IU](#CodedUITestEditor_LocateUIControl) identifica la ubicación del control en la interfaz de usuario de la aplicación sometida a prueba.  
  
9. [Localizar todos](#CodedUITestEditor_LocateDecendants) le ayuda a comprobar la propiedad del control y los cambios importantes efectuados en los controles de la aplicación.  
  
## ¿Cómo lo hago?  
 En [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], si abre el archivo UIMap.uitest asociado a la prueba de IU codificada en el proyecto de prueba de IU codificada, se mostrará automáticamente la prueba de IU codificada en el editor de pruebas de IU codificadas. En los siguientes procedimientos se describe cómo se pueden localizar y editar los métodos de prueba, las propiedades de acciones de la interfaz de usuario y los controles mediante la barra de herramientas y los menús contextuales del editor.  
  
## Abrir una prueba de IU codificada  
 Puede ver y editar la prueba de IU codificada basada en Visual C\# y Visual Basic mediante el editor de pruebas de IU codificadas.  
  
 ![Menú contextual Editar con el generador de pruebas de IU codificadas](../test/media/editcodeduitest.png "EditCodedUITest")  
  
 En el Explorador de soluciones, abra el menú contextual de **UIMap.uitest** y elija **Abrir**. La prueba de IU codificada se abre en el editor. Ahora puede ver y editar los métodos grabados, las acciones y los controles correspondientes en la prueba de IU codificada.  
  
> [!TIP]
>  Al seleccionar una acción de la interfaz de usuario ubicada en un método del panel **Acciones de IU**, el control correspondiente queda resaltado. También puede modificar la acción de la interfaz de usuario o las propiedades de los controles.  
  
 *No veo* el editor de pruebas de IU codificadas.  
 Posiblemente usa una versión de Visual Studio Enterprise anterior a la 2012. El editor de pruebas de IU codificadas también estaba disponible en el Feature Pack 2 de Visual Studio 2010 con una suscripción a MSDN.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)] [Microsoft Visual Studio 2010 Feature Pack 2](http://go.microsoft.com/fwlink/?LinkID=204119).  
  
##  <a name="CodedUITestEditor_EditActionAndControlProperties"></a> Modificar las propiedades de las acciones de la interfaz de usuario y sus propiedades de control correspondientes  
 Con el editor de pruebas de IU codificadas puede localizar y ver rápidamente todas las acciones de la interfaz de usuario en los métodos de prueba. Al seleccionar la acción de la interfaz de usuario en el editor, se resalta automáticamente el control correspondiente. Del mismo modo, si selecciona un control, se resaltan las acciones de la interfaz de usuario asociadas. Al seleccionar una acción de la interfaz de usuario o un control, es muy sencillo usar la ventana Propiedades para modificar las propiedades correspondientes.  
  
 ![Propiedades de acción de IU](../test/media/codeduiedituiaction.png "CodedUIEditUIAction")  
Editar propiedades de acción de IU  
  
 Para modificar las propiedades de una acción de la interfaz de usuario, en el panel **Acción de IU**, expanda el método de prueba que contenga una acción de la interfaz de usuario de la que desee modificar las propiedades, seleccione la acción de la interfaz de usuario y, después, modifique las propiedades mediante la ventana Propiedades.  
  
 Por ejemplo, si un servidor no está disponible y tiene una acción de la interfaz de usuario asociada al explorador web que indica **Ir a la página web "http:\/\/Contoso1\/default.aspx"**, puede cambiar la dirección URL por `‘http://Contoso2/default.aspx’`.  
  
 ![Propiedades del control](../test/media/codeduitestcontrolprop.png "CodedUITestControlProp")  
Editar las propiedades de los controles  
  
 Modificar las propiedades de un control se hace de la misma manera que se modifican las acciones de interfaz de usuario. En el panel **Asignación de controles de IU**, seleccione el control que desea editar y modifique sus propiedades en la ventana Propiedades.  
  
 Por ejemplo, un desarrollador puede haber cambiado la propiedad **\(ID\)** en un control de botón en el código fuente de la aplicación que se prueba de "idSubmit" a "idLogin". Con la propiedad **\(ID\)** cambiada en la aplicación, la prueba de IU codificada no encontrará el control de botón y se producirá un error. En este caso, el evaluador puede abrir la colección **Propiedades de búsqueda** y cambiar la propiedad **Id** para que coincida con el valor nuevo usado por el programador en la aplicación. El evaluador también podría cambiar el valor de la propiedad **Nombre descriptivo** de "Enviar" a "Iniciar sesión". Si realiza este cambio, la acción de la interfaz de usuario asociada en el editor de pruebas de IU codificadas se actualiza de "Elegir el botón 'Enviar'" a "Elegir el botón 'Iniciar sesión'".  
  
 Tras completar las modificaciones, guarde los cambios en el archivo UIMap.Designer eligiendo **Guardar** en la barra de herramientas de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 *¿Qué más debería saber?*  
 **Sugerencias**  
  
-   ![Sugerencia](../test/media/tip.png "Tip") Si no se muestra la ventana Propiedades, mantenga pulsada la tecla **Alt** mientras presiona **ENTRAR** o, como alternativa, presione **F4**.  
  
-   ![Sugerencia](../test/media/tip.png "Tip") Para deshacer los cambios de propiedad realizados, seleccione **Deshacer** desde el menú **Editar** o presione CTRL\+Z.  
  
-   ![Sugerencia](../test/media/tip.png "Tip") Puede usar el botón **Buscar** de la barra de herramientas del editor de pruebas de IU codificadas para abrir la herramienta Buscar y reemplazar en Visual Studio. Después puede usar el control Buscar para localizar una acción de la interfaz de usuario en el editor de pruebas de IU codificadas. Por ejemplo, puede intentar buscar "Hacer clic en el botón 'Inicio de sesión'". Esto puede ser útil en las pruebas de gran tamaño. Tenga en cuenta que no puede usar la funcionalidad de reemplazo en la herramienta Buscar y reemplazar del editor de pruebas de IU codificadas. Para obtener más información, consulte el control Buscar en [Buscar y reemplazar texto](../ide/finding-and-replacing-text.md).  
  
-   ![Sugerencia](../test/media/tip.png "Tip") En ocasiones puede ser difícil visualizar dónde se ubican los controles en la interfaz de usuario de la aplicación sometida a prueba. Una de las capacidades del editor de pruebas de IU codificadas es que puede seleccionar un control de la asignación de controles de IU y ver su ubicación en la aplicación sometida a prueba.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Buscar un control de interfaz de usuario en la aplicación sometida a prueba](#CodedUITestEditor_LocateUIControl), que se encuentra en un apartado posterior de este tema.  
  
-   ![Sugerencia](../test/media/tip.png "Tip") Es posible que sea necesario expandir el control de contenedor que contiene el control que quiere editar.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Buscar un control y sus descendientes](#CodedUITestEditor_LocateDecendants), que se encuentra en un apartado posterior de este tema.  
  
##  <a name="CodedUITestEditor_DeleteUIActions"></a> Eliminar acciones de IU no deseadas  
 Puede quitar fácilmente las acciones de interfaz de usuario no deseadas en la prueba de IU codificada.  
  
 ![Eliminar acción de IU](../test/media/codeduideleteuiaction.png "CodedUIDeleteUIAction")  
  
 En el panel **Acción de IU**, expanda el método de prueba que contiene la acción de la interfaz de usuario que desea eliminar. Abra el menú contextual de la acción de la interfaz de usuario y elija **Eliminar**.  
  
##  <a name="CodedUITestEditor_SplitMethods"></a> Dividir un método de prueba en dos métodos independientes  
 Puede dividir un método de prueba para refinar o modularizar las acciones de la interfaz de usuario. Por ejemplo, la prueba podría tener un solo método de prueba con acciones de la interfaz de usuario en dos controles de contenedor. Las acciones de la interfaz de usuario podrían estar más modularizadas en dos métodos que se corresponden con un contenedor.  
  
 ![Dividir un método de prueba](../test/media/codeduitestsplitmethod1.png "CodedUITestSplitMethod1")  
  
 ![Dos métodos de prueba](../test/media/codeduitestsplitmethod2.png "CodedUITestSplitMethod2")  
  
 En el panel **Acción de IU**, expanda el método de prueba que quiere dividir en dos métodos independientes y seleccione la acción de la interfaz de usuario donde quiere que comience el nuevo método de prueba. Abra el menú contextual de la acción de la interfaz de usuario y, después, elija **Dividir en un nuevo método** o elija el botón **Dividir en un nuevo método** en la barra de herramientas del editor de pruebas de IU codificadas. El nuevo método de prueba aparece en el panel Acciones de la interfaz de usuario. Contiene las acciones de la interfaz de usuario de la acción en la que especificó la división.  
  
 Una vez que haya acabado de dividir el método, guarde los cambios en el archivo UIMap.Designer eligiendo **Guardar** en la barra de herramientas de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 *¿Qué más debería saber?*  
 **Problemas importantes**  
  
-   ![Icono Precaución](../test/media/caution.png "caution") **Advertencia:** Si divide un método, debe modificar todos los códigos que llamen al método existente para llamar también al método nuevo que va a crear, en el caso de que quiera seguir incluyendo dichas acciones de interfaz de usuario. Al dividir un método se abre un cuadro de diálogo de Microsoft Visual Studio. Le advierte que debe modificar cualquier código que llame al método existente para llamar también al método nuevo que va a crear. Elija **Sí**.  
  
 **Sugerencias**  
  
-   ![Sugerencia](../test/media/tip.png "Tip") Para deshacer la división, elija **Deshacer** desde el menú **Editar** o presione CTRL\+Z.  
  
-   ![Sugerencia](../test/media/tip.png "Tip") Puede cambiar el nombre del método nuevo. Selecciónelo desde el panel Acciones de la interfaz de usuario y elija el botón **Cambiar nombre** de la barra de herramientas del editor de pruebas de IU codificadas.  
  
     O bien  
  
     Abra el menú contextual del nuevo método de prueba y elija **Cambiar nombre**.  
  
     Se abrirá el cuadro de diálogo Microsoft Visual Studio. Le advierte que debe modificar todos los códigos que hagan referencia al método. Elija **Sí**.  
  
##  <a name="CodedUITestEditor_MoveMethods"></a> Mover un método de prueba al archivo UIMap para facilitar la personalización  
 Si determina que uno de los métodos de prueba de la prueba de la interfaz de usuario codificada requiere un código personalizado, debe moverlo al archivo UIMap.cs o UIMap.vb. De lo contrario, el código se sobrescribirá cada vez que se vuelva a compilar la prueba de IU codificada. Si no mueve el método, el código personalizado se sobrescribirá cada vez que se vuelva a compilar la prueba.  
  
 En el panel **Acción de IU**, seleccione el método de prueba que quiere mover al archivo UIMap.cs o UIMap.vb para facilitar la funcionalidad de código personalizado que no se sobrescribirá cuando se vuelva a compilar el código de prueba. Después, elija el botón **Mover código**, situado en la barra de herramientas del editor de pruebas de IU codificadas, o abra el menú contextual del método de prueba y elija **Mover código**. El método de prueba se quita del archivo UIMap.uitest y ya no se muestra en el panel de acciones de la interfaz de usuario. Para editar el archivo de prueba que ha movido, abra el archivo UIMap.cs o UIMap.vb desde el Explorador de soluciones.  
  
 Una vez que haya terminado de mover el método, guarde los cambios en el archivo UIMap.Designer eligiendo **Guardar** en la barra de herramientas de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 *¿Qué más debería saber?*  
 **Problemas importantes**  
  
-   ![Icono Precaución](../test/media/caution.png "caution") **Advertencia:** Una vez que haya movido un método, ya no puede modificarlo con el editor de pruebas de IU codificadas. Debe agregar el código personalizado y mantenerlo con el Editor de código. Al mover un método se abre un cuadro de diálogo de Microsoft Visual Studio. Advierte de que el método se va a mover del archivo UIMap.uitest al archivo UIMap.cs o UIMap.vb y ya no podrá modificarlo en el editor de pruebas de IU codificadas. Elija **Sí**.  
  
 **Sugerencias**  
  
-   ![Sugerencia](../test/media/tip.png "Tip") Para deshacer el cambio, seleccione **Deshacer** en el menú **Editar** o presione Ctrl\+Z. Después también debe quitar el código manualmente desde el archivo UIMap.cs o UIMap.vb.  
  
##  <a name="CodedUITestEditor_LocateUIControl"></a> Buscar un control de interfaz de usuario en la aplicación sometida a prueba  
 En ocasiones puede ser difícil visualizar dónde se ubican los controles en la interfaz de usuario de la aplicación sometida a prueba. Una de las capacidades del editor de pruebas de IU codificadas es que puede seleccionar un control de la asignación de controles de IU y ver su ubicación en la aplicación sometida a prueba. También se puede usar la característica **Buscar control de IU** de la aplicación sometida a prueba para comprobar las modificaciones de propiedades de búsqueda que haya efectuado en un control.  
  
 ![Buscar control de IU](../test/media/codeduilocatecontrol.png "CodedUILocateControl")  
  
 ![Control encontrado en aplicación en pruebas](../test/media/codeduilocatecontrol2.png "CodedUILocateControl2")  
  
 En el panel **Asignación de controles de IU**, seleccione el control que quiere buscar en la aplicación asociada a la prueba. Después, abra el menú contextual del control y elija **Buscar control de IU**. En la aplicación que está probando, el control se marca con un borde azul.  
  
 *¿Qué más debería saber?*  
 **Problemas importantes**  
  
-   ![Icono Precaución](../test/media/caution.png "caution") **Advertencia:** Antes de buscar un control de interfaz de usuario, compruebe que se esté ejecutando la aplicación asociada a la prueba.  
  
 **Sugerencias**  
  
-   ![Sugerencia](../test/media/tip.png "Tip") Como alternativa, puede usar la opción **Buscar todos** para comprobar que se puedan buscar correctamente todos los controles de un contenedor. Esta opción se describe en la siguiente sección.  
  
##  <a name="CodedUITestEditor_LocateDecendants"></a> Buscar un control y sus descendientes  
 Puede comprobar que todos los controles de un contenedor se pueden buscar correctamente en la interfaz de usuario de la aplicación sometida a prueba. Esto puede resultar útil para comprobar los cambios en las propiedades de búsqueda que haya hecho en el contenedor. Además, si ha habido cambios significativos en la interfaz de usuario de la aplicación sometida a prueba, puede validar que las propiedades de búsqueda existentes del control sigan siendo correctas.  
  
 ![Buscar todos los controles descendientes](../test/media/codeduilocateall.png "CodedUILocateAll")  
  
 ![Todos los controles encontrados](../test/media/codeduilocateall2.png "CodedUILocateAll2")  
  
 En el panel **Asignación de controles de IU**, seleccione el control de contenedor que quiera buscar y del que quiera ver todos los descendientes. Después, abra el menú contextual del control y elija **Buscar todos**. El control contenedor y sus controles descendiente están marcados en el editor de pruebas de IU codificadas con una marca de verificación verde o una 'X' roja. Estas marcas le permiten saber si los controles se han localizado correctamente en la aplicación sometida a prueba.  
  
 *¿Qué más debería saber?*  
 **Problemas importantes**  
  
-   ![Icono Precaución](../test/media/caution.png "caution") **Advertencia:** Antes de buscar los controles de interfaz de usuario, compruebe que se esté ejecutando la aplicación asociada a la prueba.  
  
##  <a name="CodedUITestEditor_InsertDelay"></a> Insertar un retraso antes de una acción de IU  
 A veces, es posible que quiera que la prueba espere a que se produzcan ciertos eventos, como que se muestre una ventana, que se oculte la barra de progreso, etc. Con el editor de pruebas de IU codificadas puede hacerlo; para ello, inserte un retraso antes de una acción de la interfaz de usuario. Puede especificar el intervalo de retraso \(en segundos\).  
  
 ![Insertar retraso antes de una acción de IU](../test/media/codeduidelay.png "CodedUIDelay")  
  
 ![Retraso agregado con 5 segundos](../test/media/codeduidealy2.png "CodedUIDealy2")  
  
 En el panel **Acción de IU**, expanda el método de prueba que contiene la acción de la interfaz de usuario antes de la que quiere insertar un retraso. Seleccione la acción de IU. Después, abra el menú contextual de la acción de la interfaz de usuario y elija **Insertar retraso antes**. Se inserta un retraso y se resalta antes de la acción de la interfaz de usuario seleccionada con el siguiente texto: **Esperar durante 1 segundos al retraso del usuario entre acciones**. En la ventana Propiedades, cambie el valor de la propiedad **Retraso** con el número deseado de milisegundos.  
  
 Una vez que haya insertado el retraso, guarde los cambios en el archivo UIMap.Designer eligiendo **Guardar** en la barra de herramientas de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 *¿Qué más debería saber?*  
 **Notas**  
  
-   ![Requisito previo](../test/media/prereq.png "Prereq") Si necesita asegurarse de que un control determinado esté disponible antes de realizar una acción de la interfaz de usuario, considere la posibilidad de agregar código personalizado al método de prueba con el método UITestControl.WaitForControlXXX\(\) adecuado.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Hacer que la prueba de IU codificada espere por eventos concretos durante la reproducción](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).  
  
 **Sugerencias**  
  
-   ![Sugerencia](../test/media/tip.png "Tip") Si no se muestra la ventana Propiedades, mantenga pulsada la tecla Alt mientras presiona ENTRAR o, como alternativa, presione F4.  
  
## Recursos externos  
  
### Orientación  
 [Pruebas de entrega continua con Visual Studio 2012. Capítulo 2: Pruebas unitarias: Prueba del interior](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
### Preguntas más frecuentes  
 [Preguntas más frecuentes sobre las pruebas de IU codificadas \- 1](http://go.microsoft.com/fwlink/?LinkID=230576)  
  
 [Preguntas más frecuentes sobre las pruebas de IU codificadas \- 2](http://go.microsoft.com/fwlink/?LinkID=230578)  
  
### Foro  
 [Pruebas de automatización de la interfaz de usuario de Visual Studio \(incluyen CodedUI\)](http://go.microsoft.com/fwlink/?LinkID=224497)  
  
## Vea también  
 [Usar la automatización de IU para probar el código](../test/use-ui-automation-to-test-your-code.md)   
 [Crear pruebas de IU codificadas](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Crear una prueba de IU codificada controlada por datos](../test/creating-a-data-driven-coded-ui-test.md)   
 [Generar una prueba de IU codificada a partir de la grabación de acciones existente](/devops-test-docs/test/generating-a-coded-ui-test-from-an-existing-action-recording)   
 [Tutorial: Crear, modificar y mantener una prueba de IU codificada](../Topic/Walkthrough:%20Creating,%20Editing%20and%20Maintaining%20a%20Coded%20UI%20Test.md)