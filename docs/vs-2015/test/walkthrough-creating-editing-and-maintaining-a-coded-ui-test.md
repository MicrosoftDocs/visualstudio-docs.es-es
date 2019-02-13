---
title: 'Tutorial: Crear, modificar y mantener una prueba de IU codificada | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: f7c25ba7-5c9c-455b-9242-701cda56f90c
caps.latest.revision: 43
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c110ace4eba116c578d9d675eeafe4f678ac9d5d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54792238"
---
# <a name="walkthrough-creating-editing-and-maintaining-a-coded-ui-test"></a>Tutorial: Crear, modificar y mantener una prueba de IU codificada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tutorial, creará una aplicación Windows Presentation Foundation (WPF) simple para mostrar cómo crear, modificar y mantener una prueba del IU codificada. El tutorial proporciona soluciones para la corrección de pruebas que han sido interrumpidas por diversos problemas de sincronización y de control de refactorización.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para este tutorial, necesitará:  
  
-   Visual Studio Enterprise  
  
### <a name="create-a-simple-wpf-application"></a>Crear una aplicación de WPF sencilla  
  
1.  En el menú **Archivo**, elija **Nuevo** y después seleccione **Proyecto**.  
  
     Aparecerá el cuadro de diálogo **Nuevo proyecto** .  
  
2.  En el panel **Instalado**, expanda **Visual C#** y después seleccione **Escritorio de Windows**.  
  
3.  Encima del panel central, compruebe que la lista desplegable de plataforma de destino se establece en **.NET Framework 4.5**.  
  
4.  En el panel central, seleccione la plantilla **Aplicación WPF**.  
  
5.  En el cuadro de texto **Nombre**, escriba **SimpleWPFApp**.  
  
6.  Elija la carpeta donde guardará el proyecto. En el cuadro de texto **Ubicación**, escriba el nombre de la carpeta.  
  
7.  Elija **Aceptar**.  
  
     Se abre WPF Designer para Visual Studio y se muestra MainWindow del proyecto.  
  
8.  Abra el cuadro de herramientas, si aún no está abierto. Elija el menú **Ver** y después **Cuadro de herramientas**.  
  
9. Bajo la sección **Todos los controles de WPF**, arrastre un control **Botón**, **Casilla** y **Barra de progreso** hacia MainWindow en la superficie de diseño.  
  
10. Seleccione el control de botón. En la ventana Propiedades, cambie el valor de la propiedad **Nombre** de \<Sin nombre> a button1. A continuación, cambie el valor de la propiedad **Contenido** de Botón a Inicio.  
  
11. Seleccione el control ProgressBar. En la ventana Propiedades, cambie el valor de la propiedad **Nombre** de \<Sin nombre> a progressBar1. A continuación, cambie el valor de la propiedad **Máxima** de **100** a **10000**.  
  
12. Seleccione el control Checkbox. En la ventana Propiedades, cambie el valor de la propiedad **Nombre** de \<Sin nombre> a checkBox1 y desactive la propiedad **IsEnabled**.  
  
     ![Aplicación de WPF sencilla](../test/media/codedui-wpfapp.png "CodedUI_WPFApp")  
  
13. Haga doble clic en el control de botón para agregar un controlador de evento Click.  
  
     MainWindow.xmal.cs se muestra en el Editor de código con el cursor en el nuevo método button1_Click.  
  
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
  
### <a name="verify-the-wpf-application-runs-correctly"></a>Comprobar que la aplicación WPF se ejecuta correctamente  
  
1.  En el menú **Depurar**, seleccione **Iniciar depuración** o presione **F5**.  
  
2.  Observe que el control de casilla está deshabilitado. Elija **Iniciar**.  
  
     En unos segundos, la barra de progreso debería ser 100% completado.  
  
3.  Ahora puede seleccionar el control de casilla.  
  
4.  Cierre SimpleWPFApp.  
  
### <a name="create-and-run-a-coded-ui-test-for-simplewpfapp"></a>Crear y ejecutar una prueba del IU codificada para SimpleWPFApp  
  
1.  Busque la aplicación SimpleWPFApp que creó anteriormente. De forma predeterminada, la aplicación se encontrará en C:\Users\\<nombreDeUsuario\>\Documents\Visual Studio \<versión>\Projects\SimpleWPFApp\SimpleWPFApp\bin\Debug\SimpleWPFApp.exe  
  
2.  Cree un acceso directo en el escritorio a la aplicación SimpleWPFApp. Haga clic con el botón derecho en SimpleWPFApp.exe y elija **Copiar**. En el escritorio, haga clic con el botón derecho y elija **Pegar acceso directo**.  
  
    > [!TIP]
    >  Un acceso directo a la aplicación facilita el poder agregar o modificar pruebas de IU codificadas para la aplicación porque permite iniciar la aplicación rápidamente.  
  
3.  En el Explorador de soluciones, haga clic con el botón derecho en la solución, elija **Agregar** y, a continuación, seleccione **Nuevo proyecto**.  
  
     Aparece el cuadro de diálogo **Agregar nuevo proyecto** .  
  
4.  En el panel **Instalado**, expanda **Visual C#** y, a continuación, seleccione **Prueba**.  
  
5.  En el panel central, seleccione la plantilla **Proyecto de prueba de IU codificada**.  
  
6.  Elija **Aceptar**.  
  
     En el Explorador de soluciones, el nuevo proyecto de prueba de IU codificada **CodedUITestProject1** se agrega a la solución.  
  
     Aparece el cuadro de diálogo **Generar código para prueba de IU codificada**.  
  
7.  Seleccione la opción **Grabar acciones, editar asignación de IU o agregar aserciones** y elija **Aceptar**.  
  
     Aparece UIMap – Generador de pruebas de IU codificadas y la ventana de Visual Studio se minimiza.  
  
     Para obtener más información acerca de las opciones del cuadro de diálogo, vea [Crear pruebas de IU codificadas](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).  
  
8.  Elija **Iniciar grabación** en UIMap – Generador de pruebas de IU codificadas.  
  
     ![Iniciar la grabación](../test/media/cuit-builder-record.png "CUIT_Builder_Record")  
  
     Puede pausar la grabación si es necesario, por ejemplo, si tiene que encargarse del correo entrante.  
  
     ![Pausar la grabación](../test/media/cuit.png "CUIT_")  
  
    > [!WARNING]
    >  Todas las acciones realizadas en el escritorio se grabarán. Pause la grabación si está realizando acciones que puedan hacer que los datos confidenciales se incluyan en la grabación.  
  
9. Inicie SimpleWPFApp mediante el acceso directorio del escritorio.  
  
     Como antes, observe que el control de casilla está deshabilitado.  
  
10. En SimpleWPFApp, elija **Iniciar**.  
  
     En unos segundos, la barra de progreso debería ser 100% completado.  
  
11. Active el control de casilla ahora que está habilitado.  
  
12. Cierre la aplicación SimpleWPFApp.  
  
13. En UIMap - Generador de pruebas de IU codificadas, elija **Generar código**.  
  
14. En el nombre del método, escriba **SimpleAppTest** y elija **Agregar y generar**. En unos segundos, aparece la prueba de IU codificada y se agrega a la Solución.  
  
15. Cierre UIMap – Generador de pruebas de IU codificadas.  
  
     El archivo CodedUITest1.cs aparece en el Editor de código.  
  
16. Guarde el proyecto.  
  
### <a name="run-the-coded-ui-test"></a>Ejecutar la prueba de IU codificada  
  
1.  En el menú **Prueba**, seleccione **Ventanas** y después elija **Explorador de pruebas**.  
  
2.  En el menú **Compilar** , elija **Compilar solución**.  
  
3.  En el archivo CodedUITest1.cs, busque el método **CodedUITestMethod**, haga clic con el botón derecho y seleccione **Ejecutar pruebas** o ejecute la prueba desde el Explorador de pruebas.  
  
     Mientras se ejecuta la prueba de IU codificada, la aplicación SimpleWPFApp está visible. Realiza los pasos que realizó en el procedimiento anterior. Sin embargo, cuando la prueba intenta activar la casilla para el control de casilla, la ventana Resultados de pruebas muestra que se produjo un error en la prueba. Esto es debido a que la prueba intenta activar la casilla, pero no tiene en cuenta que el control de casilla está deshabilitado hasta que la barra de progreso sea 100 % completado. Puede corregir esto y los problemas similares utilizando los distintos métodos `UITestControl.WaitForControlXXX()` que están disponibles para las pruebas de IU codificadas. El procedimiento siguiente mostrará cómo utilizar el método `WaitForControlEnabled()` para corregir el problema que provocó errores en esta prueba. Para obtener más información, vea [Hacer que la prueba de IU codificada espere por eventos concretos durante la reproducción](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).  
  
### <a name="edit-and-rerun-the-coded-ui-test"></a>Modificar y volver a ejecutar la prueba de IU codificada  
  
1.  En la ventana Explorador de pruebas, seleccione la prueba con errores en la sección **Seguimiento de la pila** y elija el primer vínculo a **UIMap.SimpleAppTest()**.  
  
2.  El archivo UIMap.Designer.cs empieza con el punto de error resaltado en el código:  
  
    ```csharp  
  
    // Select 'CheckBox' check box  
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;  
    ```  
  
3.  Para corregir este problema, puede hacer que la prueba de IU codificada espere a que el control CheckBox esté habilitado antes de continuar en esta línea utilizando el método `WaitForControlEnabled()`.  
  
    > [!WARNING]
    >  No modifique el archivo UIMap.Designer.cs. Cualquier cambio que se realice en el código del archivo UIMapDesigner.cs se sobrescribirá cada vez que se genere código mediante UIMap - Generador de pruebas de IU codificadas. Si tiene que modificar un método grabado, debe copiarlo en el archivo UIMap.cs y cambiar el nombre. El archivo UIMap.cs se puede utilizar para invalidar métodos y propiedades en el archivo UIMapDesigner.cs. Debe quitar la referencia al método original en el archivo UITest.cs el Codificado y reemplazarlo con el nombre del método cuyo nombre ha cambiado.  
  
4.  En el Explorador de soluciones, busque **UIMap.uitest** en el proyecto de prueba de IU codificada.  
  
5.  Abra el menú contextual para **UIMap.uitest** y elija **Abrir**.  
  
     La prueba de IU codificada se abre en el editor. Ahora puede ver y modificar la prueba de IU codificada.  
  
6.  En el panel **Acción de UI**, seleccione el método de prueba (SimpleAppTest) que quiera mover al archivo UIMap.cs o UIMap.vb para facilitar la funcionalidad de código personalizado que no se sobrescribirá cuando se vuelva a compilar el código de prueba.  
  
7.  Elija el botón **Mover código** de la barra de herramientas del Editor de pruebas de IU codificadas.  
  
8.  Se abrirá el cuadro de diálogo Microsoft Visual Studio. Advierte de que el método se va a mover del archivo UIMap.uitest al archivo UIMap.cs y ya no podrá modificarlo en el Editor de pruebas de IU codificadas. Elija **Sí**.  
  
     El método de prueba se quita del archivo UIMap.uitest y ya no se muestra en el panel de acciones de la interfaz de usuario. Para editar el archivo de prueba que se ha movido, abra el archivo UIMap.cs en el Explorador de soluciones.  
  
9. En la barra de herramientas de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], elija **Guardar**.  
  
     Las actualizaciones del método de prueba se guardan en el archivo UIMap.Designer.  
  
    > [!CAUTION]
    >  Una vez que se ha movido el método, ya no puede modificarlo con el Editor de pruebas de la interfaz de usuario codificadas. Debe agregar el código personalizado y mantenerlo con el Editor de código.  
  
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
  
13. En el archivo CodedUITest1.cs, busque el método **CodedUITestMethod** y marque como comentario o cambie el nombre de la referencia al método original SimpleAppTest () y, a continuación, reemplácelo por el nuevo método ModifiedSimpleAppTest ():  
  
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
  
14. En el menú **COMPILAR**, elija **Compilar solución**.  
  
15. Haga clic con el botón derecho en el método **CodedUITestMethod** y seleccione **Ejecutar pruebas**.  
  
16. Esta vez, la prueba de IU codificada completa correctamente todos los pasos en la prueba y aparece **Superada** en la ventana Explorador de pruebas.  
  
### <a name="refactor-a-control-in-the-simplewpfapp"></a>Refactorizar un control en SimpleWPFApp  
  
1.  En el archivo MainWindow.xaml, en el Diseñador, seleccione el control de botón.  
  
2.  En la parte superior de la ventana Propiedades, cambie el valor de la propiedad **Nombre** de button1 a buttonA.  
  
3.  En el menú **COMPILAR**, elija **Compilar solución**.  
  
4.  En el Explorador de pruebas, ejecute **CodedUITestMethod1**.  
  
     La prueba no se supera porque la prueba de IU codificada no puede localizar el control de botón que se asignó originalmente en UIMap como button1. La refactorización puede impactar las pruebas de IU codificadas de esta manera.  
  
5.  En la ventana Explorador de pruebas, en la sección **Seguimiento de la pila**, elija el primer vínculo al lado de **UIMpa.ModifiedSimpleAppTest()**.  
  
     El archivo UIMap.cs se abre. El punto de error se resalta en el código:  
  
    ```csharp  
  
    // Click 'Start' button  
    Mouse.Click(uIStartButton, new Point(27, 10));  
    ```  
  
     Observe que la línea de código anterior en este procedimiento está utilizando `UiStartButton`, que es el nombre de UIMap antes de refactorizarse.  
  
     Para corregir el problema, puede agregar el control refactorizado a UIMap utilizando el Generador de pruebas de IU codificadas. Puede actualizar el código de la prueba para utilizar el código, tal y como se muestra en el procedimiento siguiente.  
  
### <a name="map-refactored-control-and-edit-and-rerun-the-coded-ui-test"></a>Asignar control refactorizado, y editar y volver a ejecutar la prueba de IU codificada  
  
1.  En el archivo CodedUITest1.cs, en el método **CodedUITestMethod1 ()**, haga clic con el botón derecho, seleccione **Generar código para prueba de IU codificada** y, a continuación, elija **Usar generador de pruebas de IU codificadas**.  
  
     Aparece UIMap – Generador de pruebas de IU codificadas.  
  
2.  Use el acceso directo en el escritorio que creó anteriormente; ejecute la aplicación SimpleWPFApp que creó anteriormente.  
  
3.  En UIMap – Generador de pruebas de IU codificadas, arrastre la herramienta en forma de cruz hacia el botón **Inicio** en SimpleWPFApp.  
  
     El botón **Inicio** se incluye en un cuadro azul y el Generador de pruebas de IU codificadas tarda unos segundos en procesar los datos para el control seleccionado y muestra las propiedades de los controles. Observe que **AutomationUId** se denomina **buttonA**.  
  
4.  En las propiedades para el control, elija la flecha de la esquina superior izquierda para expandir la asignación de controles de IU. Observe que **UIStartButton1** está seleccionado.  
  
5.  En la barra de herramientas, elija **Agregar control a la asignación de controles de IU**.  
  
     El estado en la parte inferior de la ventana comprueba la acción mostrando **El control seleccionado se ha agregado a la asignación de controles de IU**.  
  
6.  En UIMap - Generador de pruebas de IU codificadas, elija **Generar código**.  
  
     El Generador de pruebas de IU codificadas - Generar código aparece con una nota que indica que no se requiere ningún nuevo método y ese código únicamente se generará para los cambios a la asignación de controles de IU.  
  
7.  Elija **Generar**.  
  
8.  Cierre SimpleWPFApp.exe.  
  
9. Cierre UIMap - Generador de pruebas de IU codificadas.  
  
     UIMap – Generador de pruebas de IU codificadas tarda unos segundos en procesar los cambios en la asignación de controles de IU.  
  
10. En el Explorador de soluciones, abra el archivo UIMap.Designer.cs.  
  
11. En el archivo UIMap.Designer.cs, busque la propiedad UIStartButton1. Observe que `SearchProperties` está establecido en `"buttonA"`:  
  
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
  
     Ahora puede modificar la prueba de IU codificada para utilizar el control asignado recientemente. Como se indicó en el procedimiento anterior si desea invalidar cualquier método o propiedad en la prueba de IU codificada, debe hacerlo en el archivo UIMap.cs.  
  
12. En el archivo UIMap.cs, agregue un constructor y especifique la propiedad `SearchProperties` de la propiedad `UIStartButton` para utilizar la propiedad `AutomationID` con un valor de `"buttonA":`  
  
    ```csharp  
  
    public UIMap()  
            {  
                this.UIMainWindowWindow.UIStartButton.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";  
            }  
  
    ```  
  
13. En el menú **COMPILAR**, elija **Compilar solución**.  
  
14. En el Explorador de pruebas, ejecute CodedUITestMethod1.  
  
     Este tiempo, la prueba de IU codificada completa correctamente todos los pasos en la prueba.  En la Ventana Resultados de pruebas, verá un estado de **Superada**.  
  
## <a name="external-resources"></a>Recursos externos  
  
### <a name="videos"></a>Vídeos  
 ![vínculo al vídeo](../data-tools/media/playvideo.gif "Reproducir vídeo")[Vídeo sobre las pruebas de IU codificadas Coded UI Tests-DeepDive-Episode1-GettingStarted](http://go.microsoft.com/fwlink/?LinkID=230573)  
  
 ![vínculo al vídeo](../data-tools/media/playvideo.gif "Reproducir vídeo")[Vídeo sobre las pruebas de IU codificadas Coded UI Tests-DeepDive-Episode2-MaintainenceAndDebugging](http://go.microsoft.com/fwlink/?LinkID=230574)  
  
 ![vínculo al vídeo](../data-tools/media/playvideo.gif "Reproducir vídeo")[Vídeo sobre las pruebas de IU codificadas Coded UI Tests-DeepDive-Episode3-HandCoding](http://go.microsoft.com/fwlink/?LinkID=230575)  
  
### <a name="hands-on-lab"></a>Laboratorio de prácticas  
 [Práctica virtual de MSDN: Introducción a la creación de pruebas de IU codificadas con Visual Studio 2010](http://go.microsoft.com/fwlink/?LinkID=22508)  
  
### <a name="faq"></a>Preguntas más frecuentes  
 [Preguntas más frecuentes sobre las pruebas de IU codificadas - 1](http://go.microsoft.com/fwlink/?LinkID=230576)  
  
 [Preguntas más frecuentes sobre las pruebas de IU codificadas - 2](http://go.microsoft.com/fwlink/?LinkID=230578)  
  
### <a name="forum"></a>Foro  
 [Pruebas de automatización de la interfaz de usuario de Visual Studio (incluyen CodedUI)](http://go.microsoft.com/fwlink/?LinkID=224497)  
  
## <a name="see-also"></a>Vea también  
 [Usar UI Automation para probar el código](../test/use-ui-automation-to-test-your-code.md)   
 [Introducción a WPF Designer](http://msdn.microsoft.com/18e61d03-b96a-4058-a166-8ec6b3f6116b)   
 [Configuraciones y plataformas compatibles con las pruebas de IU codificadas y las grabaciones de acciones](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)   
 [Editar pruebas de IU codificadas mediante el editor de pruebas de IU codificadas](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)
