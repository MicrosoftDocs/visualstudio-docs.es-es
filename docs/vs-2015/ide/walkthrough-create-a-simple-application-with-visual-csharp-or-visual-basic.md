---
title: 'Tutorial: Crear una aplicación sencilla con Visual C# o Visual Basic | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d5e41dbf3422374add68e351da1e4b703772a3a4
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296860"
---
# <a name="walkthrough-create-a-simple-application-with-visual-c-or-visual-basic"></a>Tutorial: Crear una aplicación sencilla con Visual C# o Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tras completar este tutorial, estará familiarizado con muchas de las herramientas, cuadros de diálogo y diseñadores que puede utilizar para desarrollar aplicaciones con Visual Studio. Creará una aplicación sencilla de estilo “Hola a todos”, diseñará la interfaz de usuario, agregará código y depurará errores, mientras aprende a trabajar en el entorno de desarrollo integrado (IDE).

 Este tema contiene las siguientes secciones:

 [Configurar el IDE](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md#BKMK_ConfigureIDE)

 [Crear una aplicación sencilla](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md#BKMK_CreateApp)

 [Depurar y probar la aplicación](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md#BKMK_DebugTest)

> [!NOTE]
> Este tutorial se basa en Visual Studio Professional, que proporciona la plantilla de aplicación WPF en la que creará el proyecto de este tutorial. Visual Studio Express para escritorio de Windows también proporciona esa plantilla, pero no así Visual Studio Express para Windows y Visual Studio Express para Web. Para obtener información preliminar sobre cómo usar Visual Studio Express para Windows, visite el [Centro de desarrollo de software para aplicaciones de la Tienda Windows](https://msdn.microsoft.com/windows/apps/br229519). Para obtener información preliminar sobre cómo usar Visual Studio Express para Web, consulte [Get Started with ASP.NET](https://dotnet.microsoft.com/learn/aspnet/hello-world-tutorial/intro)(Introducción a ASP.NET). Asimismo la edición de Visual Studio y la configuración que utilice determinan los nombres y las ubicaciones de algunos elementos de la interfaz de usuario. Consulte [Personalizar la configuración de desarrollo en Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="BKMK_ConfigureIDE"></a> Configurar el IDE
 Al iniciar Visual Studio por primera vez, Visual Studio le pedirá que inicie sesión con una cuenta de servicio de Microsoft (MSA). [Inicio de sesión en Visual Studio](https://devblogs.microsoft.com/visualstudio/welcome-sign-in-to-visual-studio/). No es necesario iniciar sesión y puede hacerlo más tarde.

 Al iniciar Visual Studio, debe elegir una combinación de configuración que aplique un conjunto de personalizaciones predefinidas al IDE. Cada combinación de opciones se ha diseñado para que el desarrollo de aplicaciones le resulte más sencillo.

 Este tutorial asume que aplicó la **Configuración general de desarrollo**, lo que implica la menor cantidad de personalización del IDE. Si ya eligió C# o Visual Basic (ambas son opciones válidas), no debe cambiar la configuración.  Si desea cambiar la configuración, puede usar el **Asistente para importar y exportar configuraciones**. Consulte [Personalizar la configuración de desarrollo en Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 Después de abrir Visual Studio, puede identificar las ventanas de herramientas, los menús y barras de herramientas y el espacio de la ventana principal. Las ventanas de herramientas se acoplan a los lados izquierdo y derecho de la ventana de la aplicación, con **Inicio rápido**, la barra de menús y la barra de herramientas estándar en la parte superior. En el centro de la ventana de la aplicación está la **Página principal**. Cuando se carga una solución o un proyecto, los editores y diseñadores aparecen en el espacio donde está la **página de inicio** . Cuando desarrolle una aplicación, pasará la mayor parte del tiempo en esta área central.

 Figura 2: IDE de Visual Studio

 ![IDE con configuración general aplicada.](../ide/media/exploreide-idewithgeneralsettings.png "|::ref1::|")

 Puede crear personalizaciones adicionales en Visual Studio, como cambiar el tipo de fuente y el tamaño del texto en el editor o el tema de color del IDE, mediante el cuadro de diálogo **Opciones** . Dependiendo de la combinación de opciones que haya aplicado, puede que algunos elementos de este cuadro de diálogo no aparezcan automáticamente. Puede asegurarse de que aparezcan todas las opciones posibles activando la casilla **Mostrar todas las configuraciones** .

 Figura 3: Cuadro de diálogo Opciones

 ![Cuadro de diálogo Opciones con la opción Mostrar todas las configuraciones](../ide/media/exploreide-optionsdialogbox.png "|::ref2::|")

 En este ejemplo, cambiará el tema de color del IDE de claro a oscuro.  Puede continuar para crear un proyecto si lo desea.

#### <a name="to-change-the-color-theme-of-the-ide"></a>Para cambiar el tema de color del IDE

1. Para abrir el cuadro de diálogo **Opciones** , seleccione el menú **Herramientas** en la parte superior y, luego, el elemento **Opciones...** .

    ![Comando Opciones del menú Herramientas](../ide/media/exploreide-toolsoptionsmenu.png "|::ref3::|")

2. Cambie el **tema de color** a **Oscuro**y, a continuación, haga clic en **Aceptar**.

    ![Tema de color oscuro seleccionado](../ide/media/exploreide-darkthemeoptionsdlgbox.png "|::ref4::|")

   Los colores de Visual Studio deben coincidir con la imagen siguiente:

   ![IDE con tema oscuro aplicado](../ide/media/exploreide-darkthemeide.png "|::ref5::|")

   El tema de color usado para las imágenes en el resto de este tutorial es el tema claro. Para obtener más información sobre cómo personalizar el IDE, consulte [Personalizar la configuración de desarrollo de Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="BKMK_CreateApp"></a> Crear una aplicación sencilla

### <a name="create-the-project"></a>Crear el proyecto
 Cuando cree una aplicación en Visual Studio, primero creará un proyecto y una solución. Para este ejemplo, creará un proyecto de Windows Presentation Foundation (WPF).

##### <a name="to-create-the-wpf-project"></a>Para crear el proyecto de WPF

1. Cree un nuevo proyecto. En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto...** .

    ![En la barra de menús, seleccione Archivo, Nuevo, Proyecto](../ide/media/exploreide-filenewproject.png "|::ref6::|")

    También puede escribir **Nuevo proyecto** en el cuadro **Inicio rápido** para hacer lo mismo.

    ![En el cuadro de inicio rápido, especifique un proyecto nuevo](../ide/media/exploreide-quicklaunchnewprojectsmall.png "|::ref7::|")

2. Para elegir la plantilla Aplicación WPF de Visual C# o Visual Basic, elija en el panel izquierdo **Instaladas**, **Plantillas**, **Visual C#** , **Windows**, por ejemplo y, después, elija Aplicación WPF en el panel central.  Asigne al proyecto el nombre HelloWPFApp en la parte inferior del cuadro de diálogo Nuevo proyecto.

    ![Creación de un proyecto de WPF de Visual Basic, HelloWPFApp](../ide/media/exploreide-newprojectvb.png "|::ref8::|")

    O

    ![Crear un proyecto de&#35; WPF de Visual C, HelloWPFApp](../ide/media/exploreide-newprojectcsharp.png "|::ref9::|")

   Visual Studio crea el proyecto HelloWPFApp y la solución y el **Explorador de soluciones** muestra los distintos archivos. WPF Designer muestra una vista de diseño y una vista XAML de MainWindow.xaml en una vista en dos paneles. Puede deslizar el divisor para mostrar más o menos de cualquiera de las vistas.  Puede elegir ver solo la vista visual o solo la vista XAML. (Para obtener más información, vea [Diseñador WPF para desarrolladores de Windows Forms](https://msdn.microsoft.com/47ad0909-e89b-4996-b4ac-874d929f94ca)). Los elementos siguientes aparecen en el **Explorador de soluciones**:

   Figura 5: Elementos del proyecto

   ![Explorador de soluciones con los archivos HelloWPFApp cargados](../ide/media/exploreide-hellowpfappfiles.png "|::ref10::|")

   Después de crear el proyecto, puede personalizarlo. Mediante la ventana **Propiedades** , (que se encuentra en el menú **Ver** ), puede mostrar y cambiar las opciones de los elementos de proyecto, controles y otros elementos de una aplicación. Mediante las propiedades del proyecto y las páginas de propiedades, puede mostrar y cambiar las opciones de proyectos y soluciones.

##### <a name="to-change-the-name-of-mainwindowxaml"></a>Para cambiar el nombre de MainWindow.xaml

1. En el siguiente procedimiento, se asignará un nombre más específico a MainWindow. En el **Explorador de soluciones**, seleccione MainWindow.xaml. Debería ver la ventana **Propiedades** , pero, si no es así, elija el menú **Ver** y el elemento **Ventana de propiedades** . Cambie la propiedad **Nombre de archivo** a `Greetings.xaml`.

    ![Ventana Propiedades con nombre de archivo resaltado](../ide/media/exploreide-filenameinpropertieswindow.png "|::ref11::|")

    El**Explorador de soluciones** muestra que el nombre del archivo es ahora Greetings.xaml y, si expande el nodo MainWindow.xaml (poniendo el foco en el nodo y presionando la tecla flecha derecha), verá que el nombre de MainWindow.xaml.vb o MainWindow.xaml.cs es ahora Greetings.xaml.vb o Greetings.xaml.cs. Este archivo de código está anidado bajo el nodo del archivo .xaml para mostrar que están muy relacionados entre sí.

   > [!WARNING]
   > Este cambio produce un error que aprenderá a depurar y corregir en un paso posterior.

2. En el **Explorador de soluciones**, abra Greetings.xaml en la vista del diseñador (presionando la tecla Entrar mientras el nodo tiene el foco) y seleccione la barra de título de la ventana con el mouse.

3. En la ventana **Propiedades** , cambie el valor de la propiedad **Title** a `Greetings`.

   En la barra de título de MainWindow.xaml se lee ahora Greetings.

### <a name="design-the-user-interface-ui"></a>Diseñar la interfaz de usuario (IU)
 Agregaremos tres tipos de controles a esta aplicación: un control TextBlock, dos controles RadioButton y un control Button.

##### <a name="to-add-a-textblock-control"></a>Para agregar un control TextBlock

1. Abra la ventana **Cuadro de herramientas** eligiendo el menú **Ver** y el elemento **Cuadro de herramientas** .

2. En el **Cuadro de herramientas**, busque el control TextBlock.

    ![Cuadro de herramientas con el control TextBlock resaltado](../ide/media/exploreide-textblocktoolbox.png "|::ref12::|")

3. Agregue un control TextBlock a la superficie de diseño. Para ello, elija el elemento TextBlock y arrástrelo a la ventana en la superficie de diseño.  Centre el control cerca de la parte superior de la ventana.

   La ventana debería ser similar a la siguiente ilustración:

   Figura 7: Ventana Greetings con el control TextBlock

   ![Control TextBlock del formulario Greetings](../ide/media/exploreide-greetingswithtextblockonly.png "|::ref13::|")

   El marcado XAML debe tener un aspecto similar al siguiente:

```
<TextBlock HorizontalAlignment="Center" TextWrapping="Wrap" VerticalAlignment="Center" RenderTransformOrigin="4.08,2.312" Margin="237,57,221,238"><Run Text="TextBlock"/><InlineUIContainer><TextBlock TextWrapping="Wrap" Text="TextBlock"/>
```

##### <a name="to-customize-the-text-in-the-text-block"></a>Para personalizar el texto en el bloque de texto

1. En la vista XAML, busque el marcado de TextBlock y cambie el atributo de texto: `Text=”Select a message option and then choose the Display button.”`

2. Si TextBlock no se expande para ajustarse a la vista Diseño, amplíe el control TextBlock (con las asas de captación de los bordes) para que se muestre todo el texto.

3. Guarde los cambios presionando Ctrl-s o usando el elemento de menú **Archivo** .

   Después, agregará dos controles [RadioButton](https://msdn.microsoft.com/library/6c9ba847-eab7-4bba-9c74-6b56ef72067b) al formulario.

##### <a name="to-add-radio-buttons"></a>Para agregar botones de radio

1. En el **Cuadro de herramientas**, busque el control RadioButton.

    ![Ventana Cuadro de herramientas con el control RadioButton seleccionado](../ide/media/exploreide-radiobuttontoolbox.png "|::ref14::|")

2. Agregue dos controles RadioButton a la superficie de diseño eligiendo el elemento RadioButton y arrastrándolo a la ventana de la superficie de diseño dos veces. Además, mueva los botones (seleccionándolos y usando las teclas de dirección) para que los botones aparezcan uno junto al otro bajo el control TextBlock.

    La ventana debe ser similar a la que se muestra a continuación:

    Figura 8: RadioButtons en la ventana Greetings.

    ![Formulario Greetings con bloque de texto y dos botones de opción](../ide/media/exploreide-greetingswithradiobuttons.png "|::ref15::|")

3. En la ventana **Propiedades** del control RadioButton izquierdo, cambie la propiedad **Name** (la propiedad situada en la parte superior de la ventana **Propiedades** ) a `RadioButton1`.  Asegúrese de que seleccionó RadioButton y no la cuadrícula de fondo del formulario; el campo Tipo de la ventana de propiedades del campo Nombre debe indicar RadioButton.

4. En la ventana **Propiedades** del control RadioButton derecho, cambie la propiedad **Name** a `RadioButton2`y después guarde los cambios presionando Ctrl-s o usando el elemento de menú **Archivo** .  Asegúrese de haber seleccionado RadioButton antes de cambiar y guardar.

   Ahora puede agregar el texto para mostrar de cada control RadioButton. El procedimiento siguiente actualiza la propiedad **Content** de un control RadioButton.

##### <a name="to-add-display-text-for-each-radio-button"></a>Para agregar el texto para mostrar de cada botón de radio

1. En la superficie de diseño, abra el menú contextual de RadioButton1 presionando el botón secundario del mouse mientras selecciona RadioButton1, elija **Editar texto**y, luego, escriba `Hello`.

2. Abra el menú contextual de RadioButton2 presionando el botón secundario del mouse mientras selecciona RadioButton2, elija **Editar texto**y, luego, escriba `Goodbye`.

   El último elemento de la interfaz de usuario que agregará es un control [Button](https://msdn.microsoft.com/library/a9d8f5a5-c98c-463e-808a-5a4e63173098).

##### <a name="to-add-the-button-control"></a>Para agregar el control Button

1. En **Cuadro de herramientas**, busque el control **Botón** y, después, agréguelo a la superficie de diseño en los controles RadioButton seleccionando el botón y arrastrándolo al formulario de la vista de diseño.

2. En la vista XAML, cambie el valor de **Contenido** del control Botón de `Content=”Button”` a `Content=”Display”`y después guarde los cambios (Ctrl-s o use el menú **Archivo** .

    El marcado debería ser similar al del ejemplo siguiente: `<Button Content="Display" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75" Margin="215,204,0,0"/>`

   La ventana debería parecerse a la de la siguiente ilustración.

   Figura 9: Interfaz de usuario final de Greetings

   ![Formulario Greetings con etiquetas de control](../ide/media/exploreide-greetingswithconrollabels.png "|::ref16::|")

### <a name="add-code-to-the-display-button"></a>Agregar código al botón Mostrar
 Cuando se ejecuta esta aplicación, aparece un cuadro de mensaje después de que un usuario elija un botón de radio y, a continuación, el botón **Mostrar** . Aparecerá un cuadro de mensaje para Hello y otro para Goodbye. Para crear este comportamiento, debe agregar código al evento Button_Click en Greetings.xaml.vb o Greetings.xaml.cs.

##### <a name="add-code-to-display-message-boxes"></a>Agregar código para mostrar cuadros de mensaje

1. En la superficie de diseño, haga doble clic en el botón **Mostrar** .

     Se abre Greetings.xaml.vb o Greetings.xaml.cs con el cursor en el evento Button_Click. También puede agregar un controlador de eventos clic de la siguiente manera (si el código pegado tiene una línea en zigzag roja debajo de algún nombre, probablemente no seleccionó los controles RadioButton en la superficie de diseño y les cambió el nombre):

     Para Visual Basic, el controlador de eventos debe ser similar a:

    ```vb
    Private Sub Button_Click_1(sender As Object, e As RoutedEventArgs)

    End Sub
    ```

     Para Visual C#, el controlador de eventos debe ser similar a:

    ```csharp
    private void Button_Click_1(object sender, RoutedEventArgs e)
    {

    }
    ```

2. Para Visual Basic, escriba el código siguiente:

    ```vb
    If RadioButton1.IsChecked = True Then
        MessageBox.Show("Hello.")
    Else RadioButton2.IsChecked = True
        MessageBox.Show("Goodbye.")
    End If

    ```

     Para Visual C#, escriba el código siguiente:

    ```
    if (RadioButton1.IsChecked == true)
    {
        MessageBox.Show("Hello.");
    }
    else
    {
        RadioButton2.IsChecked = true;
        MessageBox.Show("Goodbye.");
    }
    ```

3. Guarde la aplicación.

## <a name="BKMK_DebugTest"></a> Depurar y probar la aplicación
 A continuación, depurará la aplicación para buscar errores y probar que los dos cuadros de mensaje aparecen correctamente. Las siguientes instrucciones indican cómo compilar e iniciar el depurador. Lea también [Compilar una aplicación de WPF (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c) y [Depurar WPF](../debugger/debugging-wpf.md) para obtener más información.

### <a name="find-and-fix-errors"></a>Buscar y corregir errores
 En este paso, buscará el error que se produjo anteriormente al cambiar el nombre del archivo XAML de la ventana principal.

##### <a name="to-start-debugging-and-find-the-error"></a>Para iniciar la depuración y buscar el error

1. Inicie el depurador seleccionando **Depurar**y después **Iniciar depuración**.

    ![Comando Iniciar depuración del menú Depurar](../ide/media/exploreide-startdebugging.png "|::ref17::|")

    Aparece un cuadro de diálogo que indica que se ha producido una excepción IOException: No se encuentra el recurso ‘mainwindow.xaml’.

2. Elija el botón **Aceptar** y después detenga el depurador.

    ![Comando Detener depuración del menú Depurar](../ide/media/exploreide-stopdebugging.png "|::ref18::|")

   Hemos cambiado el nombre de Mainwindow.xaml a Greetings.xaml al comienzo de este tutorial, pero el código todavía hace referencia a Mainwindow.xaml como el URI de inicio de la aplicación, por lo que el proyecto no puede iniciarse.

##### <a name="to-specify-greetingsxaml-as-the-startup-uri"></a>Para especificar Greetings.xaml como el URI de inicio

1. En el **Explorador de soluciones**, abra el archivo App.xaml (en el proyecto de C#) o el archivo Application.xaml (en el proyecto de Visual Basic) en la vista XAML (no puede abrirse en la vista Diseño). Para ello, seleccione el archivo y presione Entrar o haga doble clic en él.

2. Cambie `StartupUri="MainWindow.xaml"` a `StartupUri="Greetings.xaml"`y después guarde los cambios con Ctrl-s.

   Vuelva a iniciar el depurador (presione F5). Debería ver la ventana Greetings de la aplicación.

### <a name="to-debug-with-breakpoints"></a>Para depurar con puntos de interrupción
 Agregando algunos puntos de interrupción puede probar el código durante la depuración. Puede agregar puntos de interrupción eligiendo **Depurar** en el menú principal, luego **Alternar puntos de interrupción** o haciendo clic en el margen izquierdo del editor junto a la línea de código donde desea que se produzca la interrupción.

##### <a name="to-add-breakpoints"></a>Para agregar puntos de interrupción

1. Abra Greetings.xaml.vb o Greetings.xaml.cs y seleccione la línea siguiente: `MessageBox.Show("Hello.")`

2. Agregue un punto de interrupción en el menú seleccionando **Depurar**y después **Alternar puntos de interrupción**.

     ![Comando Alternar puntos de interrupción del menú Depurar](../ide/media/exploreide-togglebreakpoint.png "|::ref19::|")

     Aparece un círculo rojo al lado de la línea de código en el margen izquierdo de la ventana del editor.

3. Seleccione la línea siguiente: `MessageBox.Show("Goodbye.")`.

4. Presione la tecla F9 para agregar un punto de interrupción y después presione la tecla F5 para iniciar la depuración.

5. En la ventana **Greetings** , elija el botón de radio **Hello** y después elija el botón **Mostrar** .

     La línea `MessageBox.Show("Hello.")` se resalta en amarillo. En la parte inferior del IDE, las ventanas Automático, Variables locales e Inspección están acopladas juntas en el lado izquierdo, mientras que las ventanas Pila de llamadas, Puntos de interrupción, Comando, Inmediato y Salida están acopladas juntas en el lado derecho.

6. En la barra de menús, elija **Depurar**, **Paso a paso para salir**.

     La aplicación reanuda la ejecución y aparece un cuadro de mensaje con la palabra “Hello”.

7. Elija el botón **Aceptar** en el cuadro de mensaje para cerrarlo.

8. En la ventana **Greetings** , elija el botón de radio **Goodbye** y después elija el botón **Mostrar** .

     La línea `MessageBox.Show("Goodbye.")` se resalta en amarillo.

9. Elija la tecla F5 para continuar con la depuración. Cuando aparezca el cuadro de mensaje, elija el botón **Aceptar** en el cuadro de mensaje para cerrarlo.

10. Presione las teclas MAYÚS + F5 (presione MAYÚS en primer lugar y, mientras la mantiene presionada, presione F5) para detener la depuración.

11. En la barra de menús, elija **Depurar**, **Deshabilitar todos los puntos de interrupción**.

### <a name="build-a-release-version-of-the-application"></a>Compilar una versión de lanzamiento de la aplicación
 Ahora que ha comprobado que todo funciona, puede preparar una versión de lanzamiento de la aplicación.

##### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Para limpiar los archivos de solución y crear una versión de lanzamiento

1. En el menú principal, seleccione **Compilar**y, después, **Limpiar solución** para eliminar los archivos intermedios y de salida que se crearon durante las compilaciones anteriores.  Esto no es necesario, pero se limpian las salidas de compilación de depuración.

    ![El comando Limpiar solución del menú Compilar](../ide/media/exploreide-cleansolution.png "|::ref20::|")

2. Cambie la configuración de compilación de HelloWPFApp de **Depurar** a **Liberar** mediante el control de lista desplegable en la barra de herramientas (dice "Depurar" actualmente).

    ![Barra de herramientas Estándar con la versión seleccionada](../ide/media/exploreide-releaseversion.png "|::ref21::|")

3. Compile la solución con **Compilar**, **Compilar solución** o presione la tecla F6.

    ![Comando Compilar solución del menú Compilar](../ide/media/exploreide-buildsolution.png "|::ref22::|")

   ¡Enhorabuena por completar este tutorial! Puede encontrar el .exe creado en el directorio de soluciones y proyectos (... \HelloWPFApp\HelloWPFApp\bin\Release\\). Si quiere explorar más ejemplos, vea [Ejemplos de Visual Studio](../ide/visual-studio-samples.md).

## <a name="see-also"></a>Otras referencias
 [Novedades de Visual studio 2015](../what-s-new-in-visual-studio-2015.md) [Introducción al desarrollo con Visual Studio sugerencias de](../ide/get-started-developing-with-visual-studio.md) [productividad](../ide/productivity-tips-for-visual-studio.md)
