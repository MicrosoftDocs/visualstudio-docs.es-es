---
title: Creación de una prueba automatizada de IU
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: fe8bed9c1f1f8aee9ae8e6d1ba460bf226d7b818
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895527"
---
# <a name="walkthrough-create-edit-and-maintain-a-coded-ui-test"></a>Tutorial: Crear, editar y mantener una prueba automatizada de IU

En este tutorial aprenderá a crear, editar y mantener una prueba automatizada de IU para probar una aplicación de Windows Presentation Framework (WPF). En el tutorial se proporcionan soluciones para la corrección de pruebas que han sido interrumpidas por diversos problemas de sincronización y por la refactorización de controles.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="create-a-wpf-app"></a>Crear una aplicación WPF

1.  En el menú **Archivo**, elija **Nuevo** y después seleccione **Proyecto**.

     Aparecerá el cuadro de diálogo **Nuevo proyecto** .

2.  En el panel **Instalado**, expanda **Visual C#** y después seleccione **Escritorio de Windows**.

3.  Encima del panel central, compruebe que la lista desplegable de plataforma de destino se establece en **.NET Framework 4.5**.

4.  En el panel central, seleccione la plantilla **Aplicación WPF**.

5.  En el cuadro de texto **Nombre**, escriba **SimpleWPFApp**.

6.  Elija la carpeta donde guardará el proyecto. En el cuadro de texto **Ubicación**, escriba el nombre de la carpeta.

7.  Elija **Aceptar**.

     Se abre **WPF Designer para Visual Studio** y se muestra MainWindow del proyecto.

8.  Abra el cuadro de herramientas, si aún no está abierto. Elija el menú **Ver** y después **Cuadro de herramientas**.

9. Bajo la sección **Todos los controles de WPF**, arrastre un control **Botón**, **Casilla** y **Barra de progreso** hacia MainWindow en la superficie de diseño.

10. Seleccione el control **Botón**. En la ventana **Propiedades**, cambie el valor de la propiedad **Nombre** de \<Sin nombre> a button1. A continuación, cambie el valor de la propiedad **Contenido** de Botón a Inicio.

11. Seleccione el control **ProgressBar**. En la ventana **Propiedades**, cambie el valor de la propiedad **Nombre** de \<Sin nombre> a progressBar1. A continuación, cambie el valor de la propiedad **Máxima** de **100** a **10000**.

12. Seleccione el control **Checkbox**. En la ventana **Propiedades**, cambie el valor de la propiedad **Nombre** de \<Sin nombre> a checkBox1 y desactive la propiedad **IsEnabled**.

     ![Aplicación de WPF sencilla](../test/media/codedui_wpfapp.png)

13. Haga doble clic en el control de botón para agregar un controlador de evento Click.

     *MainWindow.xmal.cs* se muestra en el Editor de código con el cursor en el nuevo método button1_Click.

14. En la parte superior de la clase MainWindow, agregue un delegado. El delegado se utilizará para la barra de progreso. Para agregar el delegado, agregue el código siguiente:

    ```csharp
    public partial class MainWindow : Window
    {
            private delegate void ProgressBarDelegate(System.Windows.DependencyProperty dp, Object value);

        public MainWindow()
        {

            InitializeComponent();
        }
    ```

15. En el método button1_Click, agregue el siguiente código:

    ```csharp
    private void button1_Click(object sender, RoutedEventArgs e)
    {
        double progress = 0;

        ProgressBarDelegate updatePbDelegate =
            new ProgressBarDelegate(progressBar1.SetValue);

        do
        {
            progress ++;

            Dispatcher.Invoke(updatePbDelegate,
                System.Windows.Threading.DispatcherPriority.Background,
                new object[] { ProgressBar.ValueProperty, progress });
            progressBar1.Value = progress;
        }
        while (progressBar1.Value != progressBar1.Maximum);

        checkBox1.IsEnabled = true;
    }
    ```

16. Guarde el archivo.

### <a name="run-the-wpf-app"></a>Ejecutar la aplicación WPF

1.  En el menú **Depurar**, seleccione **Iniciar depuración** o presione **F5**.

2.  Observe que el control de casilla está deshabilitado. Elija **Iniciar**.

     En unos segundos, la barra de progreso debería ser 100% completado.

3.  Ahora puede seleccionar el control de casilla.

4.  Cierre SimpleWPFApp.

## <a name="create-a-shortcut-to-the-wpf-app"></a>Crear un acceso directo a la aplicación de WPF

1.  Busque la aplicación SimpleWPFApp que creó anteriormente.

2.  Cree un acceso directo en el escritorio a la aplicación SimpleWPFApp. Haga clic con el botón derecho en *SimpleWPFApp.exe* y elija **Copiar**. En el escritorio, haga clic con el botón derecho y elija **Pegar acceso directo**.

    > [!TIP]
    > Un acceso directo a la aplicación facilita el poder agregar o modificar pruebas automatizadas de IU para la aplicación porque permite iniciar la aplicación rápidamente.

## <a name="create-a-coded-ui-test-for-simplewpfapp"></a>Crear una prueba automatizada de IU para SimpleWPFApp

1. En el **Explorador de soluciones**, haga clic con el botón derecho en la solución, elija **Agregar** y, después, seleccione **Nuevo proyecto**.

     Aparece el cuadro de diálogo **Agregar nuevo proyecto** .

1. En el panel **Instalado**, expanda **Visual C#** y, a continuación, seleccione **Prueba**.

1. En el panel central, seleccione la plantilla **Proyecto de prueba de IU codificada**.

   > [!NOTE]
   > Si no ve la plantilla **Proyecto de prueba automatizada de IU**, necesitará [instalar el componente de prueba automatizada de IU](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component).

1. Elija **Aceptar**.

     El nuevo proyecto de prueba automatizada de IU llamado **CodedUITestProject1** se agregará a la solución.

     Aparece el cuadro de diálogo **Generar código para prueba de IU codificada**.

1. Seleccione la opción **Grabar acciones, editar asignación de IU o agregar aserciones** y elija **Aceptar**.

     Aparece el cuadro de diálogo **UIMap – Generador de pruebas automatizadas de IU** y se minimiza la ventana de Visual Studio.

     Para obtener más información sobre las opciones del cuadro de diálogo, vea [Crear pruebas automatizadas de IU](../test/use-ui-automation-to-test-your-code.md).

1. Seleccione **Iniciar grabación** en el cuadro de diálogo **UIMap – Generador de pruebas automatizadas de IU**.

     ![Iniciar la grabación](../test/media/cuit_builder_record.png)

     Puede pausar la grabación si es necesario, por ejemplo, si tiene que encargarse del correo entrante.

     ![Pausar la grabación](../test/media/cuit_.png)

    > [!WARNING]
    > Todas las acciones realizadas en el escritorio se grabarán. Pause la grabación si está realizando acciones que puedan hacer que los datos confidenciales se incluyan en la grabación.

1. Inicie SimpleWPFApp mediante el acceso directorio del escritorio.

     Como antes, observe que el control de casilla está deshabilitado.

1. En SimpleWPFApp, elija **Iniciar**.

     En unos segundos, la barra de progreso debería ser 100% completado.

1. Active el control de casilla ahora que está habilitado.

1. Cierre la aplicación SimpleWPFApp.

1. En el cuadro de diálogo **UIMap - Generador de pruebas automatizadas de IU**, elija **Generar código**.

1. En el cuadro **Nombre del método**, escriba **SimpleAppTest** y haga clic en **Agregar y generar**. En unos segundos aparecerá la prueba automatizada de IU y se agregará a la solución.

1. Cierre **UIMap - Generador de pruebas automatizadas de IU**.

     El archivo *CodedUITest1.cs* aparece en el editor de código.

1. Guarde el proyecto.

### <a name="run-the-test"></a>Ejecutar la prueba

1. En el menú **Prueba**, seleccione **Ventanas** y después elija **Explorador de pruebas**.

2. En el menú **Compilar** , elija **Compilar solución**.

3. En el archivo *CodedUITest1.cs*, busque el método **CodedUITestMethod**, haga clic con el botón derecho y seleccione **Ejecutar pruebas** o ejecute la prueba desde el **Explorador de pruebas**.

   Mientras se ejecuta la prueba de IU codificada, la aplicación SimpleWPFApp está visible. Realiza los pasos que realizó en el procedimiento anterior. Pero cuando la prueba intenta activar la casilla para el control de casilla, la ventana **Resultados de pruebas** muestra que se produjo un error en la prueba. Esto es debido a que la prueba intenta activar la casilla, pero no tiene en cuenta que el control de casilla está deshabilitado hasta que la barra de progreso sea 100 % completado. Puede corregir esto y los problemas similares utilizando los distintos métodos `UITestControl.WaitForControlXXX()` que están disponibles para las pruebas de IU codificadas. El procedimiento siguiente mostrará cómo utilizar el método `WaitForControlEnabled()` para corregir el problema que provocó errores en esta prueba. Para obtener más información, vea [Hacer que las pruebas automatizadas de IU esperen eventos concretos durante la reproducción](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).

## <a name="edit-and-rerun-the-coded-ui-test"></a>Editar y volver a ejecutar la prueba automatizada de IU

1.  En la ventana **Explorador de pruebas**, seleccione la prueba con errores en la sección **Seguimiento de la pila** y elija el primer vínculo a **UIMap.SimpleAppTest()**.

2.  Se abre el archivo *UIMap.Designer.cs* con el punto de error resaltado en el código:

    ```csharp
    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

3.  Para corregir este problema, puede hacer que la prueba de IU codificada espere a que el control CheckBox esté habilitado antes de continuar en esta línea utilizando el método `WaitForControlEnabled()`.

    > [!WARNING]
    > No modifique el archivo *UIMap.Designer.cs*. Cualquier cambio que se realice en el código se sobrescribirá cada vez que se genere código mediante **UIMap - Generador de pruebas automatizadas de IU**. Si tiene que modificar un método grabado, cópielo en el archivo *UIMap.cs* y cámbiele el nombre. El archivo *UIMap.cs* se puede usar para invalidar métodos y propiedades en el archivo *UIMapDesigner.cs*. Debe quitar la referencia al método original en el archivo *CodedUITest.cs* y reemplazarlo por el nombre del método cuyo nombre ha cambiado.

4.  En el **Explorador de soluciones**, busque *UIMap.uitest* en el proyecto de prueba automatizada de IU.

5.  Abra el menú contextual para *UIMap.uitest* y elija **Abrir**.

     La prueba de IU codificada se abre en el editor. Ahora puede ver y modificar la prueba de IU codificada.

6.  En el panel **Acción de IU**, seleccione el método de prueba (SimpleAppTest) que quiere mover al archivo *UIMap.cs* o *UIMap.vb*. Si se mueve el método a otro archivo, se podrá agregar código personalizado que no se sobrescribirá cuando se vuelva a compilar el código de prueba.

7.  Elija el botón **Mover código** de la barra de herramientas del **Editor de pruebas automatizadas de IU**.

8.  Se abrirá el cuadro de diálogo Microsoft Visual Studio. Le advierte de que el método se va a mover del archivo *UIMap.uitest* al archivo *UIMap.cs* y ya no podrá modificarlo en el Editor de pruebas automatizadas de IU. Elija **Sí**.

     El método de prueba se quita del archivo *UIMap.uitest* y ya no se muestra en el panel de acciones de la interfaz de usuario. Para editar el archivo de prueba que se ha movido, abra el archivo *UIMap.cs* en el **Explorador de soluciones**.

9. En la barra de herramientas de Visual Studio, elija **Guardar**.

     Las actualizaciones del método de prueba se guardan en el archivo *UIMap.Designer*.

    > [!WARNING]
    > Una vez que se ha movido el método, ya no puede modificarlo con el Editor de pruebas de la interfaz de usuario codificadas. Debe agregar el código personalizado y mantenerlo con el Editor de código.

10. Cambiar el método de `SimpleAppTest()` a `ModifiedSimpleAppTest()`

11. Agregue la siguiente instrucción using al archivo:

    ```csharp
    using Microsoft.VisualStudio.TestTools.UITesting.WpfControls;
    ```

12. Agregue el siguiente método `WaitForControlEnabled()` antes de la línea de código que provoca el error identificada previamente:

    ```csharp
    uICheckBoxCheckBox.WaitForControlEnabled();

    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

13. En el archivo *CodedUITest1.cs*, busque el método **CodedUITestMethod** y marque como comentario o cambie el nombre de la referencia al método original SimpleAppTest () y, después, reemplácelo por el nuevo método ModifiedSimpleAppTest ():

    ```csharp
    [TestMethod]
            public void CodedUITestMethod1()
            {
                // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
                // For more information on generated code, see http://go.microsoft.com/fwlink/?LinkId=179463
                //this.UIMap.SimpleAppTest();
                this.UIMap.ModifiedSimpleAppTest();
            }
    ```

14. En el menú **Compilar** , elija **Compilar solución**.

15. Haga clic con el botón derecho en el método **CodedUITestMethod** y seleccione **Ejecutar pruebas**.

16. Esta vez, la prueba automatizada de IU completa correctamente todos los pasos en la prueba y aparece **Superada** en la ventana **Explorador de pruebas**.

## <a name="refactor-a-control-in-simplewpfapp"></a>Refactorizar un control en SimpleWPFApp

1.  En el archivo *MainWindow.xaml*, en el diseñador, seleccione el control de botón.

2.  En la parte superior de la ventana **Propiedades**, cambie el valor de la propiedad **Nombre** de **button1** a **buttonA**.

3.  En el menú **Compilar** , elija **Compilar solución**.

4.  En el **Explorador de pruebas**, ejecute **CodedUITestMethod1**.

     La prueba no se supera porque la prueba de IU codificada no puede localizar el control de botón que se asignó originalmente en UIMap como button1. La refactorización puede impactar las pruebas de IU codificadas de esta manera.

5.  En el **Explorador de pruebas**, en la sección **Seguimiento de la pila**, elija el primer vínculo al lado de **UIMpa.ModifiedSimpleAppTest()**.

     Se abrirá el archivo *UIMap.cs*. El punto de error se resalta en el código:

    ```csharp
    // Click 'Start' button
    Mouse.Click(uIStartButton, new Point(27, 10));
    ```

     Observe que la línea de código anterior en este procedimiento está utilizando `UiStartButton`, que es el nombre de UIMap antes de refactorizarse.

     Para corregir el problema, puede agregar el control refactorizado a UIMap mediante el **Generador de pruebas automatizadas de IU**. Puede actualizar el código de la prueba para usar el código, tal y como se muestra en el procedimiento siguiente.

## <a name="map-refactored-control-rerun-the-test"></a>Asignar el control refactorizado y volver a ejecutar la prueba

1.  En el archivo *CodedUITest1.cs*, en el método **CodedUITestMethod1()**, haga clic con el botón derecho, seleccione **Generar código para prueba automatizada de IU** y, después, elija **Usar generador de pruebas automatizadas de IU**.

     Aparecerá **UIMap – Generador de pruebas automatizadas de IU**.

2.  Use el acceso directo en el escritorio que creó anteriormente; ejecute la aplicación SimpleWPFApp que creó anteriormente.

3.  En el cuadro de diálogo **UIMap – Generador de pruebas automatizadas de IU**, arrastre la herramienta en forma de cruz hacia el botón **Inicio** en SimpleWPFApp.

     El botón **Inicio** se encuentra en un cuadro azul. El **Generador de pruebas automatizadas de IU** tarda unos segundos en procesar los datos del control seleccionado y mostrar las propiedades del control. Observe que el valor de **AutomationUId** es **buttonA**.

4.  En las propiedades para el control, elija la flecha de la esquina superior izquierda para expandir la asignación de controles de IU. Observe que **UIStartButton1** está seleccionado.

5.  En la barra de herramientas, elija **Agregar control a la asignación de controles de IU**.

     El estado en la parte inferior de la ventana comprueba la acción mostrando **El control seleccionado se ha agregado a la asignación de controles de IU**.

6.  En el cuadro de diálogo **UIMap - Generador de pruebas automatizadas de IU**, elija **Generar código**.

     El cuadro de diálogo **Generador de pruebas automatizadas de IU - Generar código** aparece con una nota que indica que no se requiere ningún nuevo método y ese código únicamente se generará para los cambios a la asignación de controles de IU.

7.  Elija **Generar**.

8.  Cierre SimpleWPFApp.

9. Cierre **UIMap - Generador de pruebas automatizadas de IU**.

10. En el **Explorador de soluciones**, abra el archivo *UIMap.Designer.cs*.

11. En el archivo *UIMap.Designer.cs*, busque la propiedad **UIStartButton1**. Observe que `SearchProperties` está establecido en `"buttonA"`:

    ```csharp
    public WpfButton UIStartButton1
            {
                get
                {
                    if ((this.mUIStartButton1 == null))
                    {
                        this.mUIStartButton1 = new WpfButton(this);
                        #region Search Criteria
                        this.mUIStartButton1.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";
                        this.mUIStartButton1.WindowTitles.Add("MainWindow");
                        #endregion
                    }
                    return this.mUIStartButton1;
                }
            }
    ```

     Ahora puede modificar la prueba de IU codificada para utilizar el control asignado recientemente. Como se indicó en el procedimiento anterior si quiere invalidar cualquier método o propiedad en la prueba automatizada de IU, debe hacerlo en el archivo *UIMap.cs*.

12. En el archivo *UIMap.cs*, agregue un constructor y especifique la propiedad `SearchProperties` de la propiedad `UIStartButton` para usar la propiedad `AutomationID` con el valor `"buttonA":`

    ```csharp
    public UIMap()
            {
                this.UIMainWindowWindow.UIStartButton.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";
            }
    ```

13. En el menú **Compilar** , elija **Compilar solución**.

14. En el **Explorador de pruebas**, ejecute **CodedUITestMethod1**.

     Este tiempo, la prueba de IU codificada completa correctamente todos los pasos en la prueba. En la ventana **Resultados de la prueba** verá el estado **Superada**.

## <a name="videos"></a>Vídeos

![vínculo a vídeo](../data-tools/media/playvideo.gif) [Introducción a pruebas automatizadas de IU](http://go.microsoft.com/fwlink/?LinkID=230573)

![vínculo a vídeo](../data-tools/media/playvideo.gif) [Mantenimiento y depuración de pruebas automatizadas de IU](http://go.microsoft.com/fwlink/?LinkID=230574)

![vínculo a vídeo](../data-tools/media/playvideo.gif) [Codificación manual de pruebas automatizadas de IU](http://go.microsoft.com/fwlink/?LinkID=230575)

## <a name="faq"></a>Preguntas más frecuentes

[Preguntas frecuentes sobre las pruebas automatizadas de IU](https://social.msdn.microsoft.com/Forums/vsautotest/3a74dd2c-cef8-4923-abbf-7a91f489e6c4/faqs)

## <a name="see-also"></a>Vea también

- [Usar la automatización de la interfaz de usuario para probar el código](../test/use-ui-automation-to-test-your-code.md)
- [Configuraciones y plataformas compatibles con las pruebas automatizadas de IU y las grabaciones de acciones](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Editar pruebas automatizadas de IU con el Editor de pruebas automatizadas de IU](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)
