---
title: Aplicación Hola mundo con WPF en C#
description: Cree una aplicación sencilla de .NET de escritorio de Windows en C# con Visual Studio mediante el marco de interfaz de usuario de Windows Presentation Foundation (WPF).
ms.custom: seodec18, get-started
ms.date: 08/09/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ba8a29a75b21351d94c818837f07ff22785a07b5
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579986"
---
# <a name="tutorial-create-a-simple-application-with-c"></a>Tutorial: Crear una aplicación sencilla con C\#

Tras completar este tutorial, estará familiarizado con muchas de las herramientas, cuadros de diálogo y diseñadores que puede usar para desarrollar aplicaciones con Visual Studio. Creará una aplicación "Hola mundo", diseñará la interfaz de usuario, agregará código y depurará errores, mientras aprende a trabajar en el entorno de desarrollo integrado ([IDE](visual-studio-ide.md)).

## <a name="prerequisites"></a>Requisitos previos

::: moniker range="vs-2017"
Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?) para instalarlo de forma gratuita.
::: moniker-end
::: moniker range=">=vs-2019"

- Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/) para instalarlo de forma gratuita.
- Para este tutorial puede usar .NET Framework o .NET Core. .NET Core es el marco más reciente y moderno. .NET Core requiere la versión 16.3 de Visual Studio 2019 o posterior.
::: moniker-end

## <a name="configure-the-ide"></a>Configurar el IDE

::: moniker range="vs-2017"

Cuando abra Visual Studio por primera vez, se le pedirá que inicie sesión. Este paso es opcional en este tutorial. Después, probablemente aparezca un cuadro de diálogo que le pide que elija la configuración de desarrollo y el tema de color. Mantenga los valores predeterminados y elija **Iniciar Visual Studio**.

![Cuadro de diálogo Elegir configuración](../media/exploreide-settings.png)

Una vez que se haya iniciado Visual Studio, verá las ventanas de herramientas, los menús, las barras de herramientas y el espacio de la ventana principal. Las ventanas de herramientas se acoplan a los lados izquierdo y derecho de la ventana de la aplicación, con **Inicio rápido**, la barra de menús y la barra de herramientas estándar en la parte superior. En el centro de la ventana de la aplicación está la **Página principal**. Cuando se carga una solución o un proyecto, los editores y diseñadores aparecen en el espacio donde está la **página de inicio** . Cuando desarrolle una aplicación, pasará la mayor parte del tiempo en esta área central.

![IDE de Visual Studio 2017 con configuración general aplicada](../media/exploreide-idewithgeneralsettings.png "Captura de pantalla del IDE de Visual Studio 2017 con configuración general aplicada")

::: moniker-end

::: moniker range=">=vs-2019"

Al iniciar Visual Studio, la primera ventana que se abre es la de inicio. Haga clic en **Continuar sin código** para abrir el entorno de desarrollo. Se mostrarán las ventanas de herramientas, los menús, las barras de herramientas y el espacio de la ventana principal. Las ventanas de herramientas se acoplan a los lados izquierdo y derecho de la ventana de la aplicación, con un cuadro de búsqueda, la barra de menús y la barra de herramientas estándar en la parte superior. Cuando se carga una solución o un proyecto, los editores y diseñadores aparecen en el espacio central de la ventana de la aplicación. Cuando desarrolle una aplicación, pasará la mayor parte del tiempo en esta área central.

::: moniker-end

## <a name="create-the-project"></a>Crear el proyecto

Cuando cree una aplicación en Visual Studio, primero creará un proyecto y una solución. Para este ejemplo, creará un proyecto de Windows Presentation Foundation (WPF).

::: moniker range="vs-2017"

1. Cree un nuevo proyecto. En la barra de menús, seleccione **Archivo**  > **Nuevo** > **Proyecto**.

     ![En la barra de menús, seleccione Archivo, Nuevo, Proyecto](../media/exploreide-filenewproject.png "Captura de pantalla de la barra de menús donde se selecciona Archivo, Nuevo, Proyecto")

1. En el cuadro de diálogo **Nuevo proyecto**, seleccione la categoría **Instalados** > **Visual C#**  > **Escritorio de Windows** y, luego, seleccione la plantilla **Aplicación de WPF (.NET Framework)** . Asígnele al proyecto el nombre **HelloWPFApp** y haga clic en **Aceptar**.

     ![Plantilla de aplicación de WPF en el cuadro de diálogo Nuevo proyecto de Visual Studio](media/exploreide-newprojectcsharp.png "Captura de pantalla de la plantilla de aplicación de WPF en el cuadro de diálogo Nuevo proyecto")

::: moniker-end

::: moniker range="vs-2019"

1. Abra Visual Studio 2019.

1. En la ventana de inicio, elija **Crear proyecto**.

   ![Visualización de la ventana "Crear un proyecto"](../../get-started/media/vs-2019/start-window-create-new-project.png "Captura de pantalla de la ventana "Crear un proyecto"")

1. En la pantalla **Crear un proyecto nuevo**, busque "WPF", elija **Aplicación WPF (.NET Core)** y después seleccione **Siguiente**.

   ![Plantilla de aplicación de WPF en el cuadro de diálogo "Crear un proyecto"](media/vs-2019/exploreide-newprojectcsharp-vs2019.png "Captura de pantalla de la plantilla de aplicación de WPF en el cuadro de diálogo "Crear un proyecto"")

   > [!NOTE]
   > Es posible que encuentre dos plantillas de escritorio de WPF, una para .NET Framework y otra para .NET Core. La plantilla de .NET Core está disponible en la versión 16.3 de Visual Studio 2019 y versiones posteriores. Puede usar cualquiera de ellas para este tutorial, pero se recomienda .NET Core para el desarrollo nuevo.

1. En la pantalla siguiente, asígnele al proyecto el nombre **HelloWPFApp** y haga clic en **Crear**.

   ![Proyecto denominado "HelloWPFApp"](./media/vs-2019/exploreide-nameproject.png "Captura de pantalla de la ventana donde se asigna nombre al proyecto")

::: moniker-end

Visual Studio crea el proyecto HelloWPFApp y la solución, y el **Explorador de soluciones** muestra los distintos archivos. **WPF Designer** muestra una vista de diseño y una vista XAML de *MainWindow.xaml* en una vista en dos paneles. Puede deslizar el divisor para mostrar más o menos de cualquiera de las vistas. Puede elegir ver solo la vista visual o solo la vista XAML.

![Proyecto y solución de WPF en el IDE](media/exploreide-wpfproject-cs.png "Captura de pantalla del proyecto y la solución de WPF en el IDE")

> [!NOTE]
> Para más información sobre XAML (eXtensible Application Markup Language), consulte la página [Información general XAML (WPF)](/dotnet/framework/wpf/advanced/xaml-overview-wpf).

Después de crear el proyecto, puede personalizarlo. Para ello, elija **Ventana Propiedades** en el menú **Ver** o presione **F4**. Después, puede mostrar y cambiar las opciones de elementos de proyecto, controles y otros elementos de una aplicación.

   ![Ventana Propiedades](../media/exploreide-hellowpfappfiles.png "Captura de pantalla de la ventana Propiedades con los nombres de aplicación de archivo de WPF")   

### <a name="change-the-name-of-mainwindowxaml"></a>Cambiar el nombre de MainWindow.xaml

Asignemos a MainWindow un nombre más específico. En el **Explorador de soluciones**, haga clic con el botón derecho en *MainWindow.xaml* y seleccione **Cambiar nombre**. Cambie el nombre del archivo por *Greetings.xaml*.

## <a name="design-the-user-interface-ui"></a>Diseñar la interfaz de usuario (IU)

Si el diseñador no está abierto, seleccione *Greetings.xaml* y presione **Mayús**+**F7** para abrirlo.

Agregaremos tres tipos de controles a esta aplicación: un control <xref:System.Windows.Controls.TextBlock>, dos controles <xref:System.Windows.Controls.RadioButton> y un control <xref:System.Windows.Controls.Button>.

### <a name="add-a-textblock-control"></a>Agregar un control TextBlock

1. Presione **Ctrl**+**Q** para activar el cuadro de búsqueda y escriba **cuadro de herramientas**. Elija **Ver > Cuadro de herramientas** en la lista de resultados.

1. En el **Cuadro de herramientas**, expanda el nodo **Controles WPF comunes** para ver el control TextBlock.

     ![Cuadro de herramientas con el control TextBlock resaltado](../media/exploreide-textblocktoolbox.png "Captura de pantalla de la ventana Cuadro de herramientas con el control TextBlock resaltado")

1. Agregue un control TextBlock a la superficie de diseño. Para ello, elija el elemento **TextBlock** y arrástrelo a la ventana en la superficie de diseño. Centre el control cerca de la parte superior de la ventana. En Visual Studio 2019 y versiones posteriores, puede usar las guías de color rojo para centrar el control.

    La ventana debería ser similar a la siguiente ilustración:

    ![Control TextBlock del formulario Greetings](../media/exploreide-greetingswithtextblockonly.png "Captura de pantalla del control TextBlock en el formulario Greetings")

   El marcado XAML debe tener un aspecto similar al siguiente ejemplo:

    ```xaml
    <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
    </Grid>
    ```

### <a name="customize-the-text-in-the-text-block"></a>Personalizar el texto en el bloque de texto

1. En la vista XAML, busque el marcado de **TextBlock** y cambie el atributo **Text** de `TextBox` a `Select a message option and then choose the Display button.`.

   El marcado XAML debe tener un aspecto similar al siguiente ejemplo:

   ```xaml
   <Grid>
       <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
   </Grid>
   ```

1. Vuelva a centrar TextBlock si quiere y, luego, guarde los cambios. Para ello, presione **Ctrl+S** o use el elemento de menú **Archivo**.

Después, agregará dos controles [RadioButton](/dotnet/framework/wpf/controls/radiobutton) al formulario.

### <a name="add-radio-buttons"></a>Agregar botones de radio

1. En el **Cuadro de herramientas**, busque el control **RadioButton**.

     ![Ventana Cuadro de herramientas con el control RadioButton seleccionado](../media/exploreide-radiobuttontoolbox.png "Captura de pantalla de la ventana Cuadro de herramientas con el control RadioButton seleccionado")

1. Agregue dos controles RadioButton a la superficie de diseño. Para ello, elija el elemento **RadioButton** y arrástrelo a la ventana en la superficie de diseño. Mueva los botones (para hacerlo, selecciónelos y use las teclas de dirección) de modo que aparezcan uno junto al otro bajo el control TextBlock. Use las guías de color rojo para alinear los controles.

   La ventana debe ser similar a la que se muestra a continuación:

   ![Formulario Greetings con TextBlock y dos botones de radio](../media/exploreide-greetingswithradiobuttons.png "Captura de pantalla del formulario Greetings con TextBlock y dos botones de radio")

1. En la ventana **Propiedades** del control RadioButton izquierdo, cambie la propiedad **Name** (la propiedad situada en la parte superior de la ventana **Propiedades** ) a `HelloButton`.

    ![Ventana Propiedades de RadioButton](../media/exploreide-buttonproperties.png "Captura de pantalla de la ventana Propiedades de RadioButton")

1. En la ventana **Propiedades** del control RadioButton derecho, cambie la propiedad **Name** a `GoodbyeButton` y después guarde los cambios.

A continuación, podrá agregar el texto para mostrar de cada control RadioButton. El procedimiento siguiente actualiza la propiedad **Content** de un control RadioButton.

### <a name="add-display-text-for-each-radio-button"></a>Agregar el texto para mostrar de cada botón de radio

1. Cambie el atributo **Content** de los controles `HelloButton` y `GoodbyeButton` por `"Hello"` y `"Goodbye"` en el código XAML. El marcado XAML ahora debería ser similar al del ejemplo siguiente:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

### <a name="set-a-radio-button-to-be-checked-by-default"></a>Establecer que un botón de radio esté activado de forma predeterminada

En este paso haremos que HelloButton esté activado de forma predeterminada, de modo que siempre esté seleccionado uno de los dos botones de radio.

1. En la vista XAML, busque el marcado de HelloButton.

1. Agregue un atributo **IsChecked** y establézcalo en **True**. Específicamente, agregue `IsChecked="True"`.

   El marcado XAML ahora debería ser similar al del ejemplo siguiente:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" IsChecked="True" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

El último elemento de la interfaz de usuario que agregará es un control [Button](/dotnet/framework/wpf/controls/button).

### <a name="add-the-button-control"></a>Agregar el control Button

1. En el **Cuadro de herramientas**, busque el control **Botón** y, después, agréguelo a la superficie de diseño en los controles RadioButton. Para ello, arrástrelo al formulario de la vista de diseño. Si usa Visual Studio 2019 o una versión posterior, una línea de color rojo le ayuda a centrar el control.

1. En la vista XAML, cambie el valor de **Content** del control de botón de `Content="Button"` a `Content="Display"` y, después, guarde los cambios.

     La ventana debería parecerse a la de la siguiente ilustración.

     ![Formulario Greetings con etiquetas de control](media/exploreide-greetingswithcontrollabels-cs.png "Captura de pantalla del formulario Greetings con etiquetas de control")

   El marcado XAML ahora debería ser similar al del ejemplo siguiente:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" IsChecked="True" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
        <Button Content="Display" HorizontalAlignment="Left" Margin="377,270,0,0" VerticalAlignment="Top" Width="75"/>
   </Grid>
   ```

### <a name="add-code-to-the-display-button"></a>Agregar código al botón Mostrar

Cuando se ejecuta esta aplicación, aparece un cuadro de mensaje después de que un usuario elija un botón de radio y, luego, el botón **Display**. Aparecerá un cuadro de mensaje para Hello y otro para Goodbye. Para crear este comportamiento, deberá agregar código al evento `Button_Click` en *Greetings.xaml.cs*.

1. En la superficie de diseño, haga doble clic en el botón **Mostrar** .

     Se abre *Greetings.xaml.cs* con el cursor en el evento `Button_Click`.

    ```csharp
    private void Button_Click(object sender, RoutedEventArgs e)
    {

    }
    ```

1. Escriba el siguiente código:

    ```csharp
    if (HelloButton.IsChecked == true)
    {
         MessageBox.Show("Hello.");
    }
    else if (GoodbyeButton.IsChecked == true)
    {
        MessageBox.Show("Goodbye.");
    }
    ```

1. Guarde la aplicación.

## <a name="debug-and-test-the-application"></a>Depurar y probar la aplicación

Después, depurará la aplicación para buscar errores y probar que los dos cuadros de mensaje aparecen correctamente. Las siguientes instrucciones indican cómo compilar e iniciar el depurador, pero más adelante podría leer [Build a WPF application (WPF) [Compilar una aplicación de WPF (WPF)]](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) y [Depurar WPF](../../debugger/debugging-wpf.md) para obtener más información.

### <a name="find-and-fix-errors"></a>Buscar y corregir errores

En este paso, buscará el error que se ha producido anteriormente al cambiar el nombre del archivo *MainWindow.xaml*.

#### <a name="start-debugging-and-find-the-error"></a>Iniciar la depuración y buscar el error

1. Para iniciar el depurador, presione **F5** o seleccione **Depurar** y, a continuación, **Iniciar depuración**.

   Aparece la ventana **Modo de interrupción** y en la ventana **Salida** se indica que se ha producido una excepción IOException: No se encuentra el recurso "mainwindow.xaml".

   ![Mensaje de IOException](../media/exploreide-ioexception.png "Captura de pantalla del mensaje IOException")

1. Detenga el depurador. Para ello, elija **Depurar** > **Detener depuración**.

Hemos cambiado el nombre de *MainWindow.xaml* a *Greetings.xaml* al comienzo de este tutorial, pero el código todavía hace referencia a *MainWindow.xaml* como URI de inicio de la aplicación, por lo que el proyecto no puede iniciarse.

#### <a name="specify-greetingsxaml-as-the-startup-uri"></a>Especificar Greetings.xaml como el URI de inicio

1. En el **Explorador de soluciones**, abra el archivo *App.xaml*.

1. Cambie `StartupUri="MainWindow.xaml"` a `StartupUri="Greetings.xaml"` y después guarde los cambios.

Vuelva a iniciar el depurador (presione **F5**). Debería ver la ventana **Greetings** de la aplicación.

::: moniker range="vs-2017"
![Captura de pantalla de la aplicación en ejecución](media/exploreide-wpf-running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Captura de pantalla de la aplicación en ejecución](media/vs-2019/exploreide-wpf-running-app.png)
::: moniker-end

Ahora, cierre la ventana de la aplicación para detener la depuración.

### <a name="debug-with-breakpoints"></a>Depurar con puntos de interrupción

Puede probar el código durante la depuración. Para ello, agregue algunos puntos de interrupción. Para agregar puntos de interrupción, puede elegir **Depurar** > **Alternar puntos de interrupción**, hacer clic en el margen izquierdo del editor junto a la línea de código donde quiere que se produzca la interrupción o bien presionar **F9**.

#### <a name="add-breakpoints"></a>Agregar puntos de interrupción

1. Abra *Greetings.xaml.cs* y seleccione la línea siguiente: `MessageBox.Show("Hello.")`

1. Agregue un punto de interrupción en el menú seleccionando **Depurar**y después **Alternar puntos de interrupción**.

     Aparece un círculo rojo al lado de la línea de código en el margen izquierdo de la ventana del editor.

1. Seleccione la línea siguiente: `MessageBox.Show("Goodbye.")`.

1. Presione la tecla **F9** para agregar un punto de interrupción y, después, presione **F5** para iniciar la depuración.

1. En la ventana **Greetings** , elija el botón de radio **Hello** y después elija el botón **Mostrar** .

    La línea `MessageBox.Show("Hello.")` se resalta en amarillo. En la parte inferior del IDE, las ventanas Automático, Variables locales e Inspección están acopladas juntas en el lado izquierdo, mientras que las ventanas Pila de llamadas, Puntos de interrupción, Configuración de excepción, Comando, Inmediato y Salida están acopladas juntas en el lado derecho.

    ![Punto de interrupción en el depurador](media/exploreide-debugbreakpoint.png "Captura de pantalla del punto de interrupción en el depurador")

1. En la barra de menús, elija **Depurar** > **Paso a paso para salir**.

     La aplicación reanuda la ejecución y aparece un cuadro de mensaje con la palabra "Hello".

1. Elija el botón **Aceptar** en el cuadro de mensaje para cerrarlo.

1. En la ventana **Greetings** , elija el botón de radio **Goodbye** y después elija el botón **Mostrar** .

     La línea `MessageBox.Show("Goodbye.")` se resalta en amarillo.

1. Presione la tecla **F5** para continuar con la depuración. Cuando aparezca el cuadro de mensaje, elija el botón **Aceptar** en el cuadro de mensaje para cerrarlo.

1. Cierre la ventana de la aplicación para detener la depuración.

1. En la barra de menús, elija **Depurar** > **Deshabilitar todos los puntos de interrupción**.

### <a name="view-a-representation-of-the-ui-elements"></a>Visualización de una representación de los elementos de la interfaz de usuario

En la aplicación en ejecución, debería ver un widget que aparece en la parte superior de la ventana. Se trata de una aplicación auxiliar en tiempo de ejecución que proporciona acceso rápido a algunas características de depuración útiles. Haga clic en el primer botón, **Ir al árbol visual dinámico**. Debería ver una ventana con un árbol que contiene todos los elementos visuales de la página. Expanda los nodos para buscar los botones que ha agregado.

![Captura de pantalla de la ventana Árbol visual dinámico](media/vs-2019/exploreide-live-visual-tree.png)

### <a name="build-a-release-version-of-the-application"></a>Compilar una versión de lanzamiento de la aplicación

Ahora que ha comprobado que todo funciona, puede preparar una versión de lanzamiento de la aplicación.

1. En el menú principal, seleccione **Compilar** > **Limpiar solución** para eliminar los archivos intermedios y de salida que se han creado durante las compilaciones anteriores. Esto no es necesario, pero se limpian las salidas de compilación de depuración.

1. Cambie la configuración de compilación de HelloWPFApp de **Depurar** a **Liberar** mediante el control de lista desplegable en la barra de herramientas (dice "Depurar" actualmente).

1. Compile la solución seleccionando **Compilar** > **Compilar solución**.

Enhorabuena por completar este tutorial. Puede encontrar el *.exe* creado en el directorio de soluciones y proyectos ( *...\HelloWPFApp\HelloWPFApp\bin\Release*).

## <a name="next-steps"></a>Pasos siguientes

Enhorabuena por completar este tutorial. Para más información, continúe con los tutoriales siguientes.

> [!div class="nextstepaction"]
> [Continuar con más tutoriales de WPF](/dotnet/framework/wpf/getting-started/wpf-walkthroughs/)

## <a name="see-also"></a>Vea también

- [Sugerencias de productividad](../../ide/productivity-features.md)
